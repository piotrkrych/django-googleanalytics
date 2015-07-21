# django-googleanalytics
Automatically exported from code.google.com/p/django-googleanalytics

Documentation
# Installation

Checkout the app from the svn repo:

    svn co http://django-googleanalytics.googlecode.com/svn/trunk/google_analytics

Make sure the app is in your python path and add it to your INSTALLED_APPS settings
Add the templatetag {% googleanalytics %} where you want the google analitics code to be inserted in your templates, don't forget to load it first in each template: {% load googleanalytics_tags %}. You can use as many tags as you need and you can (optionally) specify diferent codes for each, see bellow if you want some examples: 

# Using the googleanalytics tag

Syntax:

    {% googleanalytics [account-code] %}

The simplest and tipical usage of this tag:

    {% googleanalytics %}

This just inserts in place the google analitics tracking code (this is just a cuple of html script tags) using the account code (the code that idenifies your account) specified in the GOOGLE_ANALYTICS_ACCOUNT_CODE setting. If you don't set this or set it to False the tag will be ignored and no code will be inserted (this is useful in some cases... for example I prefer to set it to False in my development local settings insted of using {% if not debug %}).

You can also explicitly pass the account code as a tag param:

    {% googleanalytics "UA-xxxxxx-x" %}

This is specially usefull if you want to track to different accounts depending on the view/template, you can use this tag as many times as you need.
About the tracking code template

The tracking code is the html code that google ask you to put on the pages to be tracked, in this app the code lives in a template (google_analitics/tracking_code.html) so you can override it if you want.
Using the legacy tracking code (urchin.js)

If you use the default template you can use the legacy tracking code.

By default the current recomended tracking code by google is used (ga.js) but if you have good reasons you can use the legacy tracking code (the old urchin.js) by setting GOOGLE_ANALYTICS_LEGACY_CODE = True, in your settings, but keep in mind that this is not recomended by google: "Please note that urchin.js will not receive feature updates and is not compatible with new features.". 
