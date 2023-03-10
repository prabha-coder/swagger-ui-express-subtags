# Swagger UI Express Subtags

This package produces a Swagger UI layout with endpoints grouped into a hierarhical list based on tags with
(optional) special delimiter characters to denote hierarchy. Delimiter characters are `|` and `:`. FYI - It's modified version of [swagger-ui-express](https://www.npmjs.com/package/swagger-ui-express). Please refer the documentation for module implementation with express.


## Usage

Install using npm:

```bash
$ npm install swagger-ui-express-subtags
```

Express setup `app.js`
```javascript
const express = require('express');
const app = express();
const swaggerUi = require('swagger-ui-express-subtags');
const swaggerDocument = require('./swagger.json');

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerDocument));
```

or if you are using Express router

```javascript
const router = require('express').Router();
const swaggerUi = require('swagger-ui-express-subtags');
const swaggerDocument = require('./swagger.json');

router.use('/api-docs', swaggerUi.serve);
router.get('/api-docs', swaggerUi.setup(swaggerDocument));
```

Open http://`<app_host>`:`<app_port>`/api-docs in your browser to view the documentation.

## Sample swagger.yaml for subtags implementation -> [Download](https://github.com/prabha-coder/swagger-ui-express-subtags/blob/main/swagger.yaml)

## Sample swagger.json for subtags implementation -> [Download](https://github.com/prabha-coder/swagger-ui-express-subtags/blob/main/swagger.json)

## Subtags output for above configuration files

<b> Swagger Configuration - 1 </b>

```yaml
tags:
- name: Pets
  description: Everything about your Pets
  externalDocs:
    description: Find out more
    url: http://swagger.io
- name: Pets|View
  description: Endpoints for getting information about pets
- name: Pets|Create
  description: Endpoints for adding pets to the directory
- name: Pets|Update
  description: Endpoints for updating pet information
- name: Pets|Delete

```

<b> Swagger UI Output - 1 </b>

![Subtags Output](https://github.com/prabha-coder/swagger-ui-express-subtags/blob/main/assets/Pet_tags_and_subtags_output.png?raw=true)

<b> Swagger Configuration - 2 </b>

```yaml
tags:
- name: Store
  description: Get information about the store
- name: Store|Orders
  description: Endpoints for managing orders in the store
- name: Store|Orders|Create
- name: Store|Orders|View
- name: Store|Orders|Delete
- name: Store|Inventory
  description: Endpoints for managing store inventory
- name: Store|Inventory|View

```

<b> Swagger UI Output - 2 </b>

![Subtags Output](https://github.com/prabha-coder/swagger-ui-express-subtags/blob/main/assets/Store_three_tree_view.png?raw=true)