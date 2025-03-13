mixpanel-python
==============================

.. image:: https://img.shields.io/pypi/v/mixpanel
    :target: https://pypi.org/project/mixpanel
    :alt: PyPI

.. image:: https://img.shields.io/pypi/pyversions/mixpanel
    :target: https://pypi.org/project/mixpanel
    :alt: PyPI - Python Version

.. image:: https://img.shields.io/pypi/dm/mixpanel
    :target: https://pypi.org/project/mixpanel
    :alt: PyPI - Downloads

.. image:: https://github.com/mixpanel/mixpanel-python/workflows/Tests/badge.svg

This is the official Mixpanel Python library. This library allows for
server-side integration of Mixpanel.

To import, export, transform, or delete your Mixpanel data, please see our
`mixpanel-utils package`_.


Installation
------------

The library can be installed using pip::

    pip install mixpanel


Getting Started
---------------

Typical usage usually looks like this::

    from mixpanel import Mixpanel

    mp = Mixpanel(YOUR_TOKEN)

    # tracks an event with certain properties
    mp.track(DISTINCT_ID, 'button clicked', {'color' : 'blue', 'size': 'large'})

    # sends an update to a user profile
    mp.people_set(DISTINCT_ID, {'$first_name' : 'Ilya', 'favorite pizza': 'margherita'})

For endpoints that require authentication (like importing historical data), you can use either the legacy API secret or service account credentials::

    # Using legacy API secret
    mp.import_data(API_KEY, DISTINCT_ID, 'button clicked', TIMESTAMP, 
                  {'color': 'blue'}, api_secret='your_api_secret')

    # Using service account credentials
    mp.import_data(API_KEY, DISTINCT_ID, 'button clicked', TIMESTAMP, 
                  {'color': 'blue'}, api_secret=('username', 'password'))

You can use an instance of the Mixpanel class for sending all of your events
and people updates.


Additional Information
----------------------

* `Help Docs`_
* `Full Documentation`_
* mixpanel-python-async_; a third party tool for sending data asynchronously
  from the tracking python process.

Authentication
-------------

For endpoints that require authentication (like ``import_data`` and ``merge``), you have two options:

1. Legacy API Secret: Use your project's API secret as a string. This method is being phased out but still works::

       mp.import_data(API_KEY, DISTINCT_ID, EVENT, TIMESTAMP, api_secret='your_api_secret')

2. Service Account: Use your service account credentials as a tuple of (username, password). This is the recommended method::

       mp.import_data(API_KEY, DISTINCT_ID, EVENT, TIMESTAMP, api_secret=('username', 'password'))

Note that the API key parameter is deprecated and will be removed in a future release.


.. |travis-badge| image:: https://travis-ci.org/mixpanel/mixpanel-python.svg?branch=master
.. _mixpanel-utils package: https://github.com/mixpanel/mixpanel-utils
.. _Help Docs: https://www.mixpanel.com/help/reference/python
.. _Full Documentation: http://mixpanel.github.io/mixpanel-python/
.. _mixpanel-python-async: https://github.com/jessepollak/mixpanel-python-async
