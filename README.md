# Maa Bhavani Dharmik Yatra

A tour and travel website for **Maa Bhavani Dharmik Yatra**, a religious tour (dharmik yatra) operator based in Ranchi, Jharkhand. Visitors can browse tour packages, see fares and details, view a photo gallery, read the terms and conditions, and contact the company.

Built with **Django** (Python), **SQLite**, and **Tailwind CSS**. The Django project is named `adishakti`.

---

## Features

- **Home page** with a landing banner, contact details, and a grid of all tour packages. Each card flips to show duration, origin, cities covered, and fares.
- **Tour details page** for every package with a short contact form.
- **About us**, **Gallery**, **Terms & Conditions** and **Contact us** pages.
- **Admin panel** to add and edit tours, gallery images, and contact messages without touching code.
- **Quick contact links** in the header: call, email, and WhatsApp.
- **Responsive layout** with a mobile navigation menu.

---

## Tech Stack

| Part | Technology |
|---|---|
| Backend | Django 4.0 (Python 3) |
| Database | SQLite |
| Styling | Tailwind CSS (via CDN) and custom CSS |
| Icons and fonts | Font Awesome, Ionicons |
| Contact form handling | Formspree |
| Image uploads | Pillow (used by Django `ImageField`) |

---

## Project Structure

```
maabhawani/
├── adishakti/            # Django project settings and root URLs
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── home/                 # Main app
│   ├── models.py         # Tour, Contact, Gallery
│   ├── views.py          # Page views
│   ├── urls.py           # App routes
│   └── admin.py          # Admin registration
├── templates/
│   ├── base.html         # Shared header and scripts
│   └── home/             # home, about, gallery, details, contact, terms
├── static/               # CSS, JS, and images
├── media/                # Uploaded tour and gallery images
├── db.sqlite3            # SQLite database
└── manage.py
```

---

## Pages and URLs

| URL | Page |
|---|---|
| `/` | Home and all tour packages |
| `/about/` | About us |
| `/gallery/` | Photo gallery |
| `/terms-condition/` | Terms and conditions |
| `/contact/` | Contact page with map |
| `/tour-details/<id>/` | Details for one tour |
| `/admin/` | Django admin panel |

---

## Data Models

**Tour**
- `title`, `origin`, `city`
- `duration` (in days)
- `sleeper_fare`, `ac_fare` (3rd A.C.)
- `image`
- `timeStamp`

**Gallery**
- `title`
- `image`

**Contact**
- `name`, `phone`, `email`, `content`
- `timeStamp`

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/piyush-x09/maabhawani.git
cd maabhawani
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

There is no `requirements.txt` yet. Install these manually:

```bash
pip install "django>=4.0,<5" pillow
```

### 4. Set up the database

The repo already includes a `db.sqlite3` file. If you want a fresh database instead:

```bash
python manage.py migrate
```

### 5. Create an admin user

```bash
python manage.py createsuperuser
```

### 6. Run the server

```bash
python manage.py runserver
```

Open http://127.0.0.1:8000/ in your browser.

---

## Adding Tours and Gallery Images

1. Go to http://127.0.0.1:8000/admin/ and log in.
2. Open **Tours** and click **Add Tour**. Fill in the title, origin, cities, duration, fares, and upload an image.
3. Open **Gallerys** to add gallery photos.
4. The new tour appears on the home page right away.

---

## Configuration Notes

- `DEBUG` is set to `True` and `ALLOWED_HOSTS` is empty. This is fine for local work only.
- Contact forms on the **Contact** and **Tour details** pages send their data to **Formspree**. To use your own form, change the form `action` URL in `templates/home/contact.html` and `templates/home/details.html`.
- The `contact` view in `home/views.py` can also save messages to the `Contact` model, and has commented-out email code. This is not connected to the current forms.

---

## Before Deploying to Production

- Move `SECRET_KEY` and any email credentials into **environment variables** and out of `settings.py`.
- Set `DEBUG = False` and add your domain to `ALLOWED_HOSTS`.
- Add a `requirements.txt` to pin package versions.
- Run `python manage.py collectstatic` and serve static and media files through a web server (Nginx, WhiteNoise, or similar).
- Add a `.gitignore` for `__pycache__/`, `*.pyc`, `db.sqlite3`, and `media/`.

---

## Author

Built by [Piyush](https://github.com/piyush-x09).
