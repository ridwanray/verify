Phone Verification Demo
========================

A phone number verification API tutorial

This app is to demonstrate how to create API endpoints for phone number verifications using Twilio SMS and pyotp in Django rest framework

To run this app on your system. Do the following:

### How to Run the app

```git clone https://github.com/ephraimbuddy/verify.git```

Change directory into the app:

```cd verify```

Create a new virtual environment

```python -m venv env```

Activate the environment

```source env/bin/activate``` On windows: ```source env/Scripts/activate```

Now install the necessary dependencies:

```pip install django djangorestframework twilio pyotp python-decouple```

Update the settings file:
First you need to signup with twilio to get your accound sd, token and phone number. After you get those things.
Create a `.env` file at the root of this app and add the twilio settings below:

    AUTH_USER_MODEL = "authentication.User"
    #Twilio
    TWILIO_PHONE = config('TWILIO_PHONE', default=None)
    TWILIO_ACCOUNT_SID = config('TWILIO_ACCOUNT_SID', default=None)
    TWILIO_AUTH_TOKEN = config('TWILIO_AUTH_TOKEN', default=None)
    
Make sure to add rest_framework,phone app and authentication app in installed apps:

    INSTALLED_APPS = [
    ....,
    'rest_framework',
    'phone.apps.PhoneConfig',
    'authentication.apps.AuthenticationConfig'
]


After installation, run the migration:

```python manage.py makemigrations```
```python manage.py migrate```

Create super user:

```python manage.py createsuperuser```

Run the App:
```python manage.py runserver```

### Endpoints:

    ^users/$ [name='user-list']
    ^users/(?P<pk>[^/.]+)/$ [name='user-detail']
    send_sms_code/
    verify_phone/
    ^phones/$ [name='phonenumber-list']
    ^phones/(?P<pk>[^/.]+)/$ [name='phonenumber-detail']
    api-auth/
