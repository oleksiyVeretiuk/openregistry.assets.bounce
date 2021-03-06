.. . Kicking page rebuild 2014-10-30 17:00:08
.. include:: defs.hrst

.. index:: Item, Parameter, Classification, CAV, Unit, registrationDetails

.. _Item:

Item
====

Schema
------

:id:
    string, auto-generated

:description:
    string, multilingual, required

    |ocdsDescription|
    A description of the goods, services to be provided.
    
    Auction subject / asset description.

:classification:
    :ref:`Classification`, required

    |ocdsDescription|
    The primary classification for the item. See the
    `itemClassificationScheme` to identify preferred classification lists,
    including CAV and GSIN.

    It is required for `classification.scheme` to be `CAV-PS` or `CPV`. The
    `classification.id` should be valid `CAV-PS` or `CPV` code.

:additionalClassifications:
    List of :ref:`Classification` objects, optional

    |ocdsDescription|
    An array of additional classifications for the item. See the
    `itemClassificationScheme` codelist for common options to use in OCDS. 
    This may also be used to present codes from an internal classification
    scheme.

    E.g.`CPVS`, `DK018`, `cadastralNumber` & `UA-EDR` can be chosen from the list.
    The codes are to be noted manually for `cadastralNumber` & `UA-EDR`.

:unit:
    :ref:`Unit`, required

    |ocdsDescription| 
    Description of the unit which the good comes in e.g.  hours, kilograms. 
    Made up of a unit name, and the value of a single unit.

:quantity:
    decimal, required

    |ocdsDescription|
    The number of units required

:address:
    :ref:`Address`, required

    Address, where the item is located.

:location:
    dictionary, optional

    Geographical coordinates of the location. Element consists of the following items:

    :latitude:
        string, required
    :longitude:
        string, required
    :elevation:
        string, optional, usually not used

    `location` usually takes precedence over `address` if both are present.

:registrationDetails:
    :ref:`registrationDetails`, required


.. _registrationDetails:

Registration Details
====================

Schema
------

:status:
    string, required

    Possible values are:

    :unknown: 
        Default value.
    :registering:
        Item is still registering.
    :complete:
        Item has already been registered.

:registrationID:
    string, optional

    The document identifier to refer to in the `paper` documentation.

    Available for mentioning in status: complete.

:registrationDate:
    :ref:`Date`, optional

    |ocdsDescription|
    The date on which the document was first published.

    Available for mentioning in status: complete.

.. _Classification:

Classification
==============

Schema
------

:scheme:
    string, required

    |ocdsDescription|
    A classification should be drawn from an existing scheme or list of
    codes.  This field is used to indicate the scheme/codelist from which
    the classification is drawn.  For line item classifications, this value
    should represent a known Item Classification Scheme wherever possible.

:id:
    string, required

    |ocdsDescription|
    The classification code drawn from the selected scheme.

:description:
    string, required

    |ocdsDescription|
    A textual description or title for the code.

:uri:
    uri, optional

    |ocdsDescription|
    A URI to identify the code. In the event individual URIs are not
    available for items in the identifier scheme this value should be left
    blank.

.. _Unit:

Unit
====

Schema
------

:code:
    string, required

    UN/CEFACT Recommendation 20 unit code.

:name:
    string, optional

    |ocdsDescription|
    Name of the unit
