---
title: MATRADE - API Reference
language_tabs: null
toc_footers:
  - "<a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>"
includes: null
search: true
---

# Endpoints Reference

## Sign Up

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "successfully created"
}
```

> Response if failed (400 Bad Request)

```json
{
    "error": true,
    "message": []
}
```

Use this endpoint to register new user.

### HTTP Request

`POST {hostname}/api/signup`

### Parameters

field        | Type   | Compulsory
------------ | ------ | ----------
name         | string | true
email        | email  | true
media_agency | string | true
phone_number | string | true

## Authorization

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "token": "your_token_string",
    "user": {
        "name": "Zaid",
        "email": "zaid@example.com",
        "agency": "Indah Water Sdn Bhd",
        "phone_number": "0189001235",
        "created_at": 1456730094
    }
}
```

Use this endpoint to login and get access token. User need to sign up first before can login.

### HTTP Request

`POST {hostname}/api/auth`

### Parameters

field       | Type   | Compulsory | Description
----------- | ------ | ---------- | ---------------------------------------
udid        | string | true       |
email       | email  | true       |
platform    | string | true       | ios, android
os_version  | string | true       | example: 9.0, 8.0, 5.0
device_id   | string | true       | device token used for push notification
device_type | string | true       | example: ipad, iphone, galaxy nexus

<aside class="success">Include token in header with Authorization: Bearer {token string} or as url parameter in order to perform request</aside>

## Screen Tracking

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "screen successfully saved"
}
```

Use this endpoint to track / log screen open by user.

### HTTP Request

`POST {hostname}/api/tracker/{android|ios}/{trade2media|myexport}`

### Example

`POST {hostname}/api/tracker/android/myexport`

### Parameters

field       | Type   | Compulsory
----------- | ------ | ----------
token       | string | true
screen_name | string | true

## Trade Statistics List (myexport)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": [
        {
            "id": 5,
            "title": "Malaysia’s Top 5 Export Destinations"
        },
        {
            "id": 6,
            "title": "Malaysia’s Top 5 Exports by Product Sectors"
        },
        Object,
        Object
    ]
}
```

Use this endpoint to get list of trade statistics

### HTTP Request

`GET {hostname}/api/tradestats`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Trade Statistics Detail (myexport)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "main_title": "Malaysia's Top 5 Export Destinations",
        "list": [
            {
                "title": "REPUBLIC OF SINGAPORE",
                "values": [
                    {
                        "subtitle": "Jan - Dec 2015 (RM Billion)",
                        "value": 108.47
                    },
                    {
                        "subtitle": "Jan - Dec 2014 (RM Billion)",
                        "value": 108.73
                    },
                    {
                        "subtitle": "Change %",
                        "value": -0.26
                    }
                ]
            },
            {
                "title": "PEOPLE'S REPUBLIC OF CHINA",
                "values": [
                    {
                        "subtitle": "Jan - Dec 2015 (RM Billion)",
                        "value": 101.53
                    },
                    {
                        "subtitle": "Jan - Dec 2014 (RM Billion)",
                        "value": 92.29
                    },
                    {
                        "subtitle": "Change %",
                        "value": 9.24
                    }
                ]
            },
            Object,
            Object
        ]
    }
}
```

Use this endpoint to get detail of trade statistics based on id

### HTTP Request

`GET {hostname}/api/tradestats/{id}`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Help Details

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "email": "communication@matrade.gov.my",
        "website": "http://www.matrade.gov.my",
        "fax": "+60362037037",
        "phone_number": "+60362077077",
        "address": "Menara MATRADE, Jalan Khidmat Usaha, Off Jalan Duta, 50480 Kuala Lumpur, MALAYSIA"
    }
}
```

Use this endpoint to get help details

### HTTP Request

`GET {hostname}/api/help`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Disclaimer Detail

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": "long text .."
}
```

Use this endpoint to get disclaimer details

### HTTP Request

`GET {hostname}/api/disclaimer`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Headline List

Contains feed from cms, joomla and MATRADE twitter

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": [
        {
            "id": 4,
            "type": "cms",
            "title": "Chong Wei tumbang pusingan pertama All England",
            "date": 1457575307,
            "description": "long text ..",
            "url": "",
            "image": "http://example.com/media/file_XGwI1457575495.jpg",
            "has_image": true
        },
        {
            "id": 707727590413312000,
            "type": "twitter",
            "title": "Sykt Msia digesa sertai INSP MIHAS2016 untuk peluang mengeksport brgn anda kpd 450 pembeli luar negara @MITIMalaysia https://t.co/O3yijhjjsK",
            "date": 1457570381,
            "description": "",
            "url": "https://twitter.com/matrade/status/707727590413312000",
            "image": "http://pbs.twimg.com/media/CdJaaVRUYAArlUe.jpg",
            "has_image": true
        },
        {
            "id": 707588164177661952,
            "type": "twitter",
            "title": "Msian companies were matched with a number of Filipinos buyers at our Int. Sourcing Programme today #INSP #ASEAN https://t.co/ftvoYgvWBB",
            "description": "",
            "date": 1457537139,
            "url": "https://twitter.com/matrade/status/707588164177661952",
            "image": "http://pbs.twimg.com/media/CdHbnVTVAAE8mkm.jpg",
            "has_image": true
        },
        {
            "id": 3,
            "type": "cms",
            "title": "PHP Training for Businessmen",
            "date": 1457515574,
            "url": "",
            "description": "300 characters approximately .. ",
            "image": "http://example.com/media/file_XXZ61457573380.jpg",
            "has_image": true
        },
        {
            "id": "3394",
            "type": "joomla",
            "description": "long text ..",
            "image": "",
            "has_image": false,
            "title": "MATRADE to Spearhead Mission for Construction, Building Materials & ICT Services in the UK ",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/press-releases/3394-matrade-to-spearhead-mission-for-construction-building-materials-ict-services-in-the-uk",
            "date": 1457107200
        },
        {
            "id": "3393",
            "type": "joomla",
            "description": "long text ..",
            "image": "",
            "has_image": false,
            "title": "Trade Talk@MATRADE: Safety Design and Sales Requirement for Furniture in the USA ",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/press-releases/3393-trade-talk-matrade-safety-design-and-sales-requirement-for-furniture-in-the-usa",
            "date": 1457020800
        },
        Object,
        Object
    ]
}
```

Use this endpoint to get disclaimer details

### HTTP Request

`GET {hostname}/api/headline`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Headline Detail (cms)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "id": 3,
        "title": "PHP Training for Businessmen",
        "description": "Long text ...",
        "description_html": "<sometag>Long text ...</sometag>",
        "date": 1457515574,
        "images": [
            "http://example.com/media/file_XXZ61457573380.jpg",
            "http://example.com/media/file_5tVO1457573395.jpg",
            "http://mexample.com/media/file_BC1b1457573408.jpg"
        ],
        "url": "http://example.com/post",
        "pdf": []
    }
}
```

> Response if Object invalid (404 Not Found)

```json
{
    "error": true,
    "message": "data not found",
    "data": null
}
```

Use this endpoint to get headline details using the id from list

### HTTP Request

`GET {hostname}/api/headline/{id}`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Headline Detail (joomla)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "id": 3400,
        "title": "Egypt Introduces New Rules on Mandatory Registration for Malaysian Factories",
        "description": "Long text ...",
        "description_html": "<sometag>Long text ...</sometag>",
        "date": 1457515574,
        "images": [],
        "url": "http://example.com/post",
        "pdf": []
    }
}
```

> Response if Object invalid (404 Not Found)

```json
{
    "error": true,
    "message": "data not found",
    "data": null
}
```

Use this endpoint to get headline details using the id from list

### HTTP Request

`GET {hostname}/api/headline/{id}/joomla`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Speeches (joomla)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": [
        {
            "id": "3320",
            "type": "joomla",
            "description": "YBHG. DATO’ DZULKIFLI MAHMUD,Chief Executive Officer of MATRADE,YB Dato’ Sri Mustapa Mohamed,Minister of International Trade and Industry (MITI),YB Dato’ Seri Ong Ka Chuan,Minister of International Trade and Industry II,YB Dato’ Lee Chee Leong,Deputy Minister (Trade) of the Ministry of ",
            "image": "",
            "has_image": false,
            "title": "Speech by CEO Matrade - Export Day 2016 (18th January 2016)",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/speeches/3320-speech-by-ceo-matrade-export-day-2016-18th-january-2016",
            "date": 1453737600
        },
        {
            "id": "3064",
            "type": "joomla",
            "description": "YB Dato’ Noraini Ahmad,Chairman of MATRADE,YB Datuk Ir. Haji Hamim Samuri & YB Dato' Lee Chee Leong,Deputy Ministers of International Trade and Industry (MITI),Distinguished Guests,Members of the Media,Ladies & Gentlemen.Bismillahirrahmannirrahim.Assalamualaikum Warahmatullahi Wabarakatuh ",
            "image": "",
            "has_image": false,
            "title": "Speech By YB Dato’ Sri Mustapa Mohamed, Minister of MITI, Launching of The MTCDP",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/speeches/3064-speech-by-yb-dato-sri-mustapa-mohamed-minister-of-miti-launching-of-the-mtcdp",
            "date": 1423670400
        },
        {
            "id": "3060",
            "type": "joomla",
            "description": "BismillahYang Berhormat Dato’ Sri Mustapa Mohamed, Minister of International Trade and Industry of MalaysiaYang Berhormat Datuk Seri Husni Hanadzlah, Minister of Finance 2 of MalaysiaYang Berhormat Datuk Ir Hamim Samuri, AndYang Berhormat Dato’ Lee Chee Leong, Deputy Ministers of International ",
            "image": "",
            "has_image": false,
            "title": "Welcoming Remarks By Y.B. Dato’ Noraini Ahmad Chairman of MATRADE At The Launching Of The Mid-Tier Companies Development Programme",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/speeches/3060-welcoming-remarks-by-y-b-dato-noraini-ahmad-chairman-of-matrade-at-the-launching-of-the-mid-tier-companies-development-programme",
            "date": 1423670400
        },
        Object,
        Object,
        Object
    ]
}
```

Use this endpoint to get list of speeches

### HTTP Request

`GET {hostname}/api/speech`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Speech Detail (joomla)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "id": 3400,
        "title": "Welcoming Remarks By Y.B. Dato’ Noraini Ahmad Chairman of MATRADE At The Launching Of The Mid-Tier Companies Development Programme",
        "description": "BismillahYang Berhormat Dato’ Sri Mustapa Mohamed, Minister of International Trade and Industry of MalaysiaYang Berhormat Datuk Seri Husni Hanadzlah, Minister of Finance 2 of MalaysiaYang Berhormat Datuk Ir Hamim Samuri, AndYang Berhormat Dato’ Lee Chee Leong, Deputy Ministers of International ...",
        "description_html": "<sometag>Long text ...</sometag>",
        "date": 1457515574,
        "images": [],
        "url": "http://example.com/post",
        "pdf": []
    }
}
```

Use this endpoint to get detail of speech by passing record id

### HTTP Request

`GET {hostname}/api/speech/{id}`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Press Release (joomla)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": [
        {
            "id": "3400",
            "type": "joomla",
            "description": "Egypt Introduces New Rules on Mandatory Registration for Malaysian FactoriesThursday, March 10th, 2016, Kuala Lumpur:  The Arab Republic of Egypt has announced through its Ministerial Decree No.43 issued on 2 February 2016 on a mandatory requirement for all foreign factories to register with the ",
            "image": "",
            "has_image": false,
            "title": "Egypt Introduces New Rules on Mandatory Registration for Malaysian Factories ",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/press-releases/3400-egypt-introduces-new-rules-on-mandatory-registration-for-malaysian-factories",
            "date": 1457564400
        },
        {
            "id": "3399",
            "type": "joomla",
            "description": "MIHAS 2016: Malaysian Companies Set to Penetrate 39 World Markets at Sourcing ProgrammeTuesday, March 5th, 2016, Kuala Lumpur:  Malaysia External Trade Development Corporation (MATRADE) in a statement urged Malaysian companies to participate in the International Sourcing Programme (INSP) to be held ",
            "image": "",
            "has_image": false,
            "title": "MIHAS 2016: Malaysian Companies Set to Penetrate 39 World Markets at Sourcing Programme",
            "url": "http://www.matrade.gov.my/en/about-matrade/media/press-releases/3399-mihas-2016-malaysian-companies-set-to-penetrate-39-world-markets-at-sourcing-programme",
            "date": 1457391600
        },
        Object,
        Object,
        Object
    ]
}
```

Use this endpoint to get list of speeches

### HTTP Request

`GET {hostname}/api/pressrelease`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true

## Press Release Detail (joomla)

> Response if success (200 OK)

```json
{
    "error": false,
    "message": "",
    "data": {
        "id": 3400,
        "title": "MATRADE to Spearhead Mission for Construction, Building Materials & ICT Services in the UK",
        "description": "long text ..",
        "description_html": "<sometag>Long text ...</sometag>",
        "date": 1457515574,
        "images": [],
        "url": "http://www.matrade.gov.my/en/about-matrade/media/press-releases/3394-matrade-to-spearhead-mission-for-construction-building-materials-ict-services-in-the-uk",
        "pdf": []
    }
}
```

Use this endpoint to get detail of speech by passing record id

### HTTP Request

`GET {hostname}/api/pressrelease/{id}`

### Parameters

field | Type   | Compulsory
----- | ------ | ----------
token | string | true
