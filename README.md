# HubSpot PHP API client


## Setup

In composer.json:

```
"require": {
	"fungku/hubspot-php": "~0.1@dev"
}
```
then run `composer install` or `composer update`

## Status

(:heavy_check_mark: Complete, :interrobang: In Progress, :x: Todo)

:x: Blog

:heavy_check_mark: Contacts

:x: Forms

:x: Keywords

:x: Lead Nurturing

:x: Leads

:x: Lists

:x: MarketPlace

:x: Properties

:x: Settings

:x: Social Media

:x: Workflows


## Quickstart


```php
$hubspot = Fungku\HubSpot\HubSpotService::create('api-key');

// Get a single contact
$contact = $hubspot->contacts()->getByEmail("test@hubspot.com");

// Get an array of 10 contacts
// getting only the firstname and lastname properties
// and set the offset to 123456
$collection = $hubspot->contacts()->all([
        'count'      => 10,
        'properties' => 'firstname, lastname',
        'vidOffset'  => 123456,
]);

foreach ($collection['contacts'] as $contact) {
    echo $contact['properties']['firstname']['value'];
}

// For pagination
echo $collection['has-more'];
echo $collection['vid-offset'];
```

*Note:* The Hubspot class checks for a `HUBSPOT_API_KEY` environment variable if you don't include one during instantiation.

I would make the syntax cleaner `$contact->firstname`, but as you can see it would probably take a lot of work. [Here is a sample](https://github.com/fungku/hubspot-php/wiki/Contact-Var-Dump) `var_dump()` of a contact. I might visit this after all the other Api classes are working, though. 