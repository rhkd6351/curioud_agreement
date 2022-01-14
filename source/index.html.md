---
title: 큐리어드 - 온라인 동의서

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  # - ruby
  # - python
  - javascript

toc_footers:
  - <a href='#'>(주) 큐리어드</a>
  - <a href='#'></a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: 큐리어드 동의서
    content: Documentation for the Curioud Agreement_project
---

# 온라인 동의서

## Introduction

host: 15.164.134.52 <br/>
port: 8080
<br/><br/>
test id: curioud1, curioud2, curioud3 <br/>
test pw: curioud1, curioud2, curioud3 <br/>

<!-- 22/01/14 문서생성 -->

# 회원관리

## Login

```shell
curl "/api/user/login" \

```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "jwt": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ0ZXN0MiIsImF1dGgiOiJST0xFX1VTRVIiLCJleHAiOjE2NDIxMzM1NTV9.b3eiLR0IgmDFIOZLqC8peN7uFPdIbo8wrSvKXO26sYNYINvh5D9fr_UOhX_VxwRZEyvuTjN_yIq_aGQhp9nzJg"
}
```

로그인, access token을 발급합니다.

### HTTP Request

`POST /api/user/login`

### Request Body

| Parameter | Type   | required | Description           |
| --------- | ------ | -------- | --------------------- |
| id        | String | true     | 유저 id 입니다.       |
| password  | String | true     | 유저 비밀번호 입니다. |

<aside class="notice">
발급된 access token은 모든 작성자 api의 header에 사용됩니다.
</aside>
<aside class="notice">
토큰의 유효시간은 2h 입니다.
</aside>

## Get User

```shell
curl "/api/user" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
  "idx": 7,
  "id": "curioud1",
  "password": "*",
  "name": "curioud1",
  "auth": "ROLE_USER",
  "reg_date": "2022-01-05T17:23:00"
}
```

회원 정보를 리턴합니다.

### HTTP Request

`GET http://15.164.134.52:8080/api/user/login`

<aside class="notice">
페이지 로드시 호출하여 토큰이 유효한지 확인해 로그인을 관리할 수 있습니다.
</aside>

## Sign Up

```shell
curl "/api/user" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
  "idx": 7,
  "id": "curioud1",
  "password": "*",
  "name": "curioud1",
  "auth": "ROLE_USER",
  "reg_date": "2022-01-05T17:23:00"
}
```

회원을 등록합니다.

### HTTP Request

`POST /api/user`

### Request Body

| Parameter | Type   | required | Description           |
| --------- | ------ | -------- | --------------------- |
| id        | String | true     | 유저 id 입니다.       |
| password  | String | true     | 유저 비밀번호 입니다. |
| name      | String | true     | 유저 이름 입니다.     |

<aside class="warning">
관리자 계정만 회원을 등록할 수 있습니다. <br/>관리자계정: ID: curioudAdmin PW: curioudAdmin
</aside>

# 작성자

## Get Project

```shell
curl "/api/project/{project-name}" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
  "idx": 1,
  "name": "83847735-4ec7-4056-83d7-bbc561af19d6",
  "title": "제출한 문서 샘플",
  "description": "test description",
  "reg_date": "2022-01-14T10:30:14",
  "end_date": null,
  "up_date": "2022-01-14T10:30:46",
  "state": 2,
  "submittee_count": 2,
  "pdf": {
    "idx": 2,
    "name": "3061683f-8b32-4d81-836e-8f7dba0752d5",
    "size": 641217,
    "extension": ".pdf",
    "url": "http://15.164.134.52:8080/api/project/pdf/3061683f-8b32-4d81-836e-8f7dba0752d5",
    "original_name": "제출한 문서 샘플-병합됨",
    "save_name": "3061683f-8b32-4d81-836e-8f7dba0752d5.pdf",
    "total_page": 2,
    "reg_date": "2022-01-14T10:30:14",
    "original_width": [2092.0, 595.32]
  },
  "project_object_checkboxes": [
    {
      "idx": 167,
      "name": null,
      "width": 32,
      "height": 45,
      "rotate": 30.5,
      "page": 1,
      "project": null,
      "color": "#000000",
      "type": "DEFAULT",
      "x_position": 50,
      "y_position": 60,
      "object_type": "OBJECT_TYPE_CHECKBOX"
    }, {...}, ...
  ],
  "project_object_texts": [
    {
      "idx": 168,
      "name": "obj1",
      "width": 310,
      "height": 410,
      "rotate": 60.5,
      "page": 1,
      "project": null,
      "color": "#000000",
      "type": "DEFAULT",
      "x_position": 160,
      "y_position": 210,
      "object_type": "OBJECT_TYPE_TEXT",
      "font_size": 24
    }, {...}, ...
  ],
  "project_object_signs": [
    {
      "idx": 164,
      "name": "obj2",
      "width": 35,
      "height": 60,
      "rotate": 10.5,
      "page": 1,
      "project": null,
      "type": "DEFAULT",
      "x_position": 120,
      "y_position": 240,
      "object_type": "OBJECT_TYPE_SIGN"
    }, {...}, ...
  ]
}
```

프로젝트 정보를 가져옵니다.<br />
프로젝트의 pdf, objects 가 포함되어있습니다.

### HTTP Request

`GET /api/project/{project-name}`

### Path Parameter

| Parameter    | Type   | Required | Description             |
| ------------ | ------ | -------- | ----------------------- |
| project-name | String | true     | 프로젝트의 name 입니다. |

<aside class="warning">
본인이 소유한 project만 가져올 수 있습니다.
</aside>

## Post Project

```shell
curl "/api/project" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
  "idx": 37,
  "name": "83847735-4ec7-4056-83d7-bbc561af19d6",
  "title": "제출한 문서 샘플-병합됨",
  "description": "test description2",
  "pdf": {
    "idx": 57,
    "name": "3061683f-8b32-4d81-836e-8f7dba0752d5",
    "size": 641217,
    "extension": ".pdf",
    "url": "http://15.164.134.52:8080/api/project/pdf/3061683f-8b32-4d81-836e-8f7dba0752d5",
    "original_name": "제출한 문서 샘플-병합됨.pdf",
    "save_name": "3061683f-8b32-4d81-836e-8f7dba0752d5.pdf",
    "total_page": 2,
    "reg_date": "2022-01-14T10:30:13.66020481"
  },
  "reg_date": "2022-01-14T10:30:13.665869355",
  "end_date": null,
  "up_date": "2022-01-14T10:30:13.6658801",
  "state": 1,
  "submittee_count": 0
}
```

새로운 프로젝트를 등록합니다.

### HTTP Request

`POST /api/project`

### Request Body

| Parameter   | Type   | Required | Description               |
| ----------- | ------ | -------- | ------------------------- |
| file_pdf    | File   | true     | 프로젝트 원본 pdf 입니다. |
| description | String | true     | 프로젝트 설명 입니다.     |

## Get Project List

```shell
curl "/api/projects" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
[
    {
        "idx": 20,
        "name": "211ebb65-df26-4bcf-aef3-b2eaceb2a16d",
        "title": "test title",
        "description": "test description",
        "reg_date": "2022-01-10T14:06:15",
        "end_date": null,
        "up_date": "2022-01-10T14:06:42",
        "state": 1,
        "submittee_count": 0
    }, {...}, ...
]
```

내가 등록한 프로젝트 List를 가져옵니다.

### HTTP Request

`GET /api/projects`

## Post Objects

```shell
curl "/api/project/{project-name}/objects" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
    "idx": 37,
    "name": "83847735-4ec7-4056-83d7-bbc561af19d6",
    "title": "제출한 문서 샘플",
    "description": "test description",
    "reg_date": "2022-01-14T10:30:14",
    "end_date": null,
    "up_date": "2022-01-14T10:30:14",
    "state": 1,
    "submittee_count": 0,
    "project_object_checkboxes": [
        {
            "idx": 166,
            "name": "obj4",
            "width": 30,
            "height": 40,
            "rotate": 20.5,
            "page": 1,
            "project": null,
            "color": "#000000",
            "type": "DEFAULT",
            "x_position": 100,
            "y_position": 200,
            "object_type": "OBJECT_TYPE_CHECKBOX"
        }, {...}, ...
    ],
    "project_object_texts": [
        {
            "idx": 168,
            "name": "obj1",
            "width": 310,
            "height": 410,
            "rotate": 60.5,
            "page": 1,
            "project": null,
            "color": "#000000",
            "type": "DEFAULT",
            "x_position": 160,
            "y_position": 210,
            "object_type": "OBJECT_TYPE_TEXT",
            "font_size": 24
        }, {...}, ...
    ],
    "project_object_signs": [
        {
            "idx": 164,
            "name": "obj2",
            "width": 35,
            "height": 60,
            "rotate": 10.5,
            "page": 1,
            "project": null,
            "type": "DEFAULT",
            "x_position": 120,
            "y_position": 240,
            "object_type": "OBJECT_TYPE_SIGN"
        }, {...}, ...
    ]
}
```

프로젝트에 오브젝트를 등록, 저장합니다.

### HTTP Request

`POST /api/project/{project-name}/objects`

### Request Body

| Parameter                 | Type  | Required | Description                    |
| ------------------------- | ----- | -------- | ------------------------------ |
| project_object_texts      | Array | true     | text 오브젝트 배열 입니다.     |
| project_object_signs      | Array | true     | sign 오브젝트 배열 입니다.     |
| project_object_checkboxes | Array | true     | checkbox 오브젝트 배열 입니다. |

project_object_texts 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |
| color      | String  | true     | 텍스트 오브젝트의 색상 입니다. ex)#000000                            |
| font_size  | Integer | true     | 텍스트 오브젝트의 폰크 크기입니다.                                   |

project_object_signs 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |

project_object_checkboxes 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |
| color      | String  | true     | 체크박스 오브젝트의 색상 입니다. ex)#000000                          |

## Get Submittees

```shell
curl "/api/project/{project-name}/submittees" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
[
    {
        "idx": 24,
        "name": "8c13ba71-3083-4534-bea7-a8051a1fb8bb",
        "activated": 1,
        "student_name": "임예광",
        "student_id": 201713984,
        "reg_date": "2022-01-14T10:30:50",
    }, {...}, ...
]
```

프로젝트의 제출자 리스트를 가져옵니다.

### HTTP Request

`GET /api/project/{project-name}/submittees`

### Path Parameter

| Parameter    | Type   | Required | Description             |
| ------------ | ------ | -------- | ----------------------- |
| project-name | String | true     | 프로젝트의 name 입니다. |

## Get Submittee

```shell
curl "/api/submittee/{submittee-name}" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
    "idx": 3,
    "name": "8c13ba71-3083-4534-bea7-a8051a1fb8bb",
    "activated": 1,
    "student_name": "임예광",
    "student_id": 201713984,
    "reg_date": "2022-01-14T10:30:50",
    "pdf": {
        "idx": 57,
        "name": "3061683f-8b32-4d81-836e-8f7dba0752d5",
        "size": 641217,
        "extension": ".pdf",
        "url": "http://15.164.134.52:8080/api/project/pdf/3061683f-8b32-4d81-836e-8f7dba0752d5",
        "original_name": "제출한 문서 샘플-병합됨.pdf",
        "save_name": "3061683f-8b32-4d81-836e-8f7dba0752d5.pdf",
        "total_page": 2,
        "reg_date": "2022-01-14T10:30:14",
        "original_width": [
            2092.0,
            595.32
        ]
    },
    "submittee_object_checkboxes": [
        {
            "idx": 85,
            "name": "checkbox1",
            "width": 30,
            "height": 40,
            "rotate": 20.5,
            "page": 1,
            "checked": false,
            "color": "#000000",
            "type": "DEFAULT",
            "x_position": 100,
            "y_position": 200,
            "object_type": "OBJECT_TYPE_CHECKBOX"
        }, {...}, ...
    ],
    "submittee_object_texts": [
        {
            "idx": 84,
            "name": "text1",
            "width": 310,
            "height": 410,
            "rotate": 60.5,
            "page": 1,
            "content": "hello",
            "color": "#000000",
            "type": "DEFAULT",
            "x_position": 160,
            "y_position": 210,
            "object_type": "OBJECT_TYPE_TEXT",
            "font_size": 24
        }, {...}, ...
    ],
    "submittee_object_signs": [
        {
            "idx": 82,
            "name": "sign1",
            "width": 35,
            "height": 60,
            "rotate": 10.5,
            "page": 1,
            "type": "DEFAULT",
            "x_position": 120,
            "y_position": 240,
            "object_type": "OBJECT_TYPE_SIGN",
            "submittee_object_sign_img": {
                "idx": 37,
                "name": "04d6b104-a274-47bd-b1e2-5645dcefc965",
                "size": 67118,
                "extension": ".png",
                "url": "http://15.164.134.52:8080/api/submittee/object/img/04d6b104-a274-47bd-b1e2-5645dcefc965",
                "original_name": "sign1.png",
                "save_name": "04d6b104-a274-47bd-b1e2-5645dcefc965.png",
                "upload_path": "*",
                "reg_date": "2022-01-14T10:30:50"
            }
        }, {...}, ...
    ]
}
```

프로젝트 제출자 정보를 가져옵니다.
원본 pdf, objects 가 포함되어있습니다.

### HTTP Request

`GET /api/submittee/{submittee-name}`

### Path Parameter

| Parameter      | Type   | Required | Description           |
| -------------- | ------ | -------- | --------------------- |
| submittee-name | String | true     | 제출자의 name 입니다. |

## Change State

```shell
curl "/api/project/{project-name}/state" \
  -H "Authorization: {token}"

```

> The above command returns JSON structured like this:

```json
{
  "message": "state changed"
}
```

프로젝트의 공유 상태를 변경할 수 있습니다. <br/>
1: 생성됨 (이 상태로의 변경은 불가능합니다)<br/>
2: 공유중 (공유 중단 상태로 변경 가능합니다.)<br/>
3: 공유중단 (공유중 상태로 변경 가능합니다.)<br/>

### HTTP Request

`PUT /api/project/{project-name}/state`

### Query Parameter

| Parameter | Type    | Required | Description                                             |
| --------- | ------- | -------- | ------------------------------------------------------- |
| state     | Integer | true     | 현재 프로젝트 상태에 따라 2 또는 3으로 변경 가능합니다. |

## Get Submittee PDF

```shell
curl "/api/project/submittee/{submittee-name}/pdf" \
  -H "Authorization: {token}"

```

> The above command returns PDF file:

제출자의 PDF를 가져옵니다.

### HTTP Request

`PUT /api/project/submittee/{submittee-name}/pdf`

### Path Parameter

| Parameter      | Type   | Required | Description                                   |
| -------------- | ------ | -------- | --------------------------------------------- |
| submittee-name | String | true     | 제출자의 이름(name, not student_name) 입니다. |

# 제출자

## Get Project

```shell
curl "/api/submittee/project/{project-name}"

```

> The above command returns JSON structured like this:

```json
{
  "idx": 1,
  "name": "83847735-4ec7-4056-83d7-bbc561af19d6",
  "title": "제출한 문서 샘플",
  "description": "test description",
  "reg_date": "2022-01-14T10:30:14",
  "end_date": null,
  "up_date": "2022-01-14T10:30:46",
  "state": 2,
  "submittee_count": 2,
  "pdf": {
    "idx": 2,
    "name": "3061683f-8b32-4d81-836e-8f7dba0752d5",
    "size": 641217,
    "extension": ".pdf",
    "url": "http://15.164.134.52:8080/api/project/pdf/3061683f-8b32-4d81-836e-8f7dba0752d5",
    "original_name": "제출한 문서 샘플-병합됨",
    "save_name": "3061683f-8b32-4d81-836e-8f7dba0752d5.pdf",
    "total_page": 2,
    "reg_date": "2022-01-14T10:30:14",
    "original_width": [2092.0, 595.32]
  },
  "project_object_checkboxes": [
    {
      "idx": 167,
      "name": null,
      "width": 32,
      "height": 45,
      "rotate": 30.5,
      "page": 1,
      "project": null,
      "color": "#000000",
      "type": "DEFAULT",
      "x_position": 50,
      "y_position": 60,
      "object_type": "OBJECT_TYPE_CHECKBOX"
    }, {...}, ...
  ],
  "project_object_texts": [
    {
      "idx": 168,
      "name": "obj1",
      "width": 310,
      "height": 410,
      "rotate": 60.5,
      "page": 1,
      "project": null,
      "color": "#000000",
      "type": "DEFAULT",
      "x_position": 160,
      "y_position": 210,
      "object_type": "OBJECT_TYPE_TEXT",
      "font_size": 24
    }, {...}, ...
  ],
  "project_object_signs": [
    {
      "idx": 164,
      "name": "obj2",
      "width": 35,
      "height": 60,
      "rotate": 10.5,
      "page": 1,
      "project": null,
      "type": "DEFAULT",
      "x_position": 120,
      "y_position": 240,
      "object_type": "OBJECT_TYPE_SIGN"
    }, {...}, ...
  ]
}
```

프로젝트 정보를 가져옵니다.<br />
프로젝트의 pdf, objects 가 포함되어있습니다.

### HTTP Request

`GET /api/submittee/project/{project-name}`

### Path Parameter

| Parameter    | Type   | Required | Description             |
| ------------ | ------ | -------- | ----------------------- |
| project-name | String | true     | 프로젝트의 name 입니다. |

<aside class="warning">
공유중 (state = 2) 인 상태의 프로젝트만 가져올 수 있습니다.
</aside>

## Submit

```shell
curl "/api/submittee/project/{project-name}"

```

> The above command returns PDF file:

```t
제출한 pdf file
```

작성이 완료된 프로젝트를 제출합니다.

### HTTP Request

`POST /api/submittee/project/{project-name}`

### Request Body

| Parameter | Type   | Required | Description                                                                                 |
| --------- | ------ | -------- | ------------------------------------------------------------------------------------------- |
| data      | Object | true     | 이름, 학번 및 작성 완료한 json object 입니다.                                               |
| sign_img  | file   | true     | sign 오브젝트의 이미지 입니다. 여러개의 파일을 같은 key값으로(sign_img) 입력할 수 있습니다. |
| file_pdf  | file   | true     | checkbox 오브젝트 배열 입니다.                                                              |

<aside class="notice">sign_img로 등록되는 이미지 파일의 이름과 sign object 요소의 이름이 정확히 일치해야 합니다. <br/>따라서 이미지 서로의 이름, sign object 서로의 이름이 달라야 합니다.</aside>
<aside class="notice">이미지는 jpg, jpeg, png 확장자만 허용합니다.</aside>

<br/>data 요소

| Parameter                   | Type    | Required | Description                                |
| --------------------------- | ------- | -------- | ------------------------------------------ |
| student_name                | String  | true     | 제출자의 이름입니다.                       |
| student_id                  | Integer | true     | 제출자의 학번입니다.                       |
| submittee_object_texts      | Array   | true     | 작성 완료된 text 오브젝트 배열 입니다.     |
| submittee_object_signs      | Array   | true     | 작성 완료된 sign 오브젝트 배열 입니다.     |
| submittee_object_checkboxes | Array   | true     | 작성 완료된 checkbox 오브젝트 배열 입니다. |

data - submittee_object_texts 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |
| color      | String  | true     | 텍스트 오브젝트의 색상 입니다. ex)#000000                            |
| font_size  | Integer | true     | 텍스트 오브젝트의 폰크 크기입니다.                                   |
| content    | String  | true     | 작성된 텍스트 오브젝트의 내용입니다.                                 |

data - submittee_object_signs 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |

data - submittee_object_checkboxes 요소

| Parameter  | Type    | Required | Description                                                          |
| ---------- | ------- | -------- | -------------------------------------------------------------------- |
| name       | String  | true     | 오브젝트의 이름 입니다.                                              |
| x_position | Integer | true     | 오브젝트의 x좌표 입니다.                                             |
| y_position | Intger  | true     | 오브젝트의 y좌표 입니다.                                             |
| width      | Intger  | true     | 오브젝트 가로길이 입니다.                                            |
| height     | Intger  | true     | 오브젝트 세로길이 입니다.                                            |
| rotate     | Float   | true     | 오브젝트 rotate 입니다.                                              |
| page       | Integer | true     | 오브젝트가 속한 pdf의 페이지 입니다.                                 |
| type       | String  | true     | 오브젝트의 타입 입니다. 사용자가 직접 커스텀하여 사용할 수 있습니다. |
| color      | String  | true     | 체크박스 오브젝트의 색상 입니다. ex)#000000                          |
| checked    | Boolean | true     | 작성된 체크박스의 체크 유무 입니다.                                  |
