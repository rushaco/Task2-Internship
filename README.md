# Django OTP Admin Integration

This project demonstrates how to integrate OTP (One-Time Password) authentication for the Django admin interface using `django_otp`. The project was developed as part of Task 2 of JP Morgan's Cybersecurity Virtual Internship.

## Project Overview

The goal of this project is to enhance the security of the Django admin interface by requiring a second factor of authentication (OTP) in addition to the usual username and password.

## Features

- OTP authentication for the admin interface
- Configuration and setup of OTP devices
- Use of TOTP (Time-based One-Time Password) for generating OTP tokens

## Installation and Setup

Follow these steps to set up and run the project locally.

### Prerequisites

- Python 3.11.9 (or any compatible version)
- Django (as specified in `requirements.txt`)
- Anaconda (optional, for managing Python environments)

### Steps

1. **Clone the Repository**
    ```sh
    git clone https://github.com/your-username/your-repository.git
    cd your-repository
    ```

2. **Set Up a Virtual Environment**
    ```sh
    conda create --name django-otp-env python=3.11.9
    conda activate django-otp-env
    ```

3. **Install Dependencies**
    ```sh
    pip install -r requirements.txt
    ```

4. **Make Migrations and Migrate**
    ```sh
    python manage.py makemigrations
    python manage.py migrate
    ```

5. **Create a Superuser**
    ```sh
    python manage.py createsuperuser
    ```

6. **Run the Development Server**
    ```sh
    python manage.py runserver
    ```

7. **Access the Admin Interface**
    - Open your web browser and navigate to `http://localhost:8000/admin/`
    - Log in with your superuser credentials

## Configuring OTP for the Admin User

### Temporarily Disable OTP Middleware

1. **Open `settings.py`**:
    - Navigate to your project directory and open the `settings.py` file.

2. **Comment Out the OTP Middleware**:
    ```python
    MIDDLEWARE = [
        ...
        # 'django_otp.middleware.OTPMiddleware',
        ...
    ]
    ```

3. **Restart the Server**:
    ```sh
    python manage.py runserver
    ```

4. **Log In to the Admin Interface**:
    - Use your superuser credentials to log in.

5. **Configure OTP for the Admin User**:
    - Go to the "Users" section in the admin interface.
    - Select your superuser account.
    - Add an OTP device and scan the QR code with an OTP app like Google Authenticator.

6. **Re-enable OTP Middleware**:
    - Uncomment the `django_otp.middleware.OTPMiddleware` line in `settings.py`.
    ```python
    MIDDLEWARE = [
        ...
        'django_otp.middleware.OTPMiddleware',
        ...
    ]
    ```

7. **Restart the Server**:
    ```sh
    python manage.py runserver
    ```

8. **Log In with OTP**:
    - Log out and then log back in using your username, password, and OTP token.

## Acknowledgments

This project was developed as Task 2 of JP Morgan's Cybersecurity Virtual Internship. Special thanks to the internship program for providing valuable learning opportunities.





