Installation
============

We assume you're familiar with `Composer <http://packagist.org>`_, a dependency manager for PHP.

Use following command to add the bundle to your `composer.json` and download package.
Simply add to your `composer.json` file:

.. code-block:: yaml

    {
        "require": {
            "sylius/omnipay-bundle": "*"
        }
    }

And run composer to update your dependencies:

.. code-block:: bash

    $ php composer.phar update

Adding required bundles to the kernel
-------------------------------------

First, you need to enable the bundle inside the kernel.

.. code-block:: php

    <?php

    // app/AppKernel.php

    public function registerBundles()
    {
        $bundles = array(
            // ...
            new FOS\RestBundle\FOSRestBundle(),
            new JMS\SerializerBundle\JMSSerializerBundle($this),

            new Sylius\Bundle\OmnipayBundle\SyliusOmnipayBundle()
        );
    }

Configuration
-------------

Put this configuration inside your ``app/config/config.yml``.

.. code-block:: yaml

    sylius_omnipay:
        gateways:
            AuthorizeNet_AIM:            # gateway name, use anyone 
                type: AuthorizeNet_AIM   # predefined list of types, read father for explanation 
                label: Authorize.Net AIM # how is gateway will be displayed in a form, etc.
            AuthorizeNet_SIM:
                type: AuthorizeNet_SIM
                label: Authorize.Net SIM
            Stripe:
                type: Stripe
                label: Stripe
                mode: true                # optional, default: false, activate test mode
                active: false             # optional, default: true, does this gateway is active
                options:                  # optional, predefine list of options to get work with gateway
                    apikey: secretapikey
            PayPal_Express:
                type: PayPal_Express
                label: PayPal Express
            PayPal_Pro:
                type: PayPal_Pro
                label: PayPal Pro

Implemented gateways
--------------------

The following gateways are already implemented:

* 2Checkout
* Authorize.Net AIM
* Authorize.Net SIM
* CardSave
* Dummy
* GoCardless
* Manual
* Netaxept (BBS)
* PayFast
* Payflow Pro
* PaymentExpress (DPS) PxPay
* PaymentExpress (DPS) PxPost
* PayPal Express Checkout
* PayPal Payments Pro
* Pin Payments
* Sage Pay Direct
* Sage Pay Server
* Stripe
* WorldPay

The above list all time is growing. Full list of supported gateways you can find at the `Omnipay <https://github.com/adrianmacneil/omnipay>`_ github repository.