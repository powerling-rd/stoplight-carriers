# Shipping labels

Shipping labels can be provided to us in response to the [delivery request](https://woop.stoplight.io/docs/carrier/branches/english/woop_to_carrier.v1.4.1.json/paths/~1deliveries/post) :

### Schema
```json json_schema
{
  "description": "Shipping label",
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Label id"
    },
    "type": {
      "type": "string",
      "description": "Sending type of label",
      "enum": ["base64", "url"]
    },
    "mode": {
      "type": "string",
      "description": "Label format",
      "enum": ["zpl", "pdf", "jpg", "jpeg"]
    },
    "value": {
      "type": "string",
      "description": "Label in base64 or url to the label"
    },
    "packageId:": {
      "type": "string",
      "description" : "Id of the associated label"
    }
  },
  "required": [
    "id"
  ],
  "title": "Label"
}
```
**Several possibilities :** 

*Label in base64*

```json
{
  "id": "LBL001",
  "type": "base64",
  "mode": "jpeg",
  "value": "UklGRvwNAABXRUJQVlA4TPANAAA...",
  "packageId": "5q4f5q4zd"
}
```

*Label by url*
```json
{
  "id": "LBL002",
  "type": "url",
  "mode": "jpeg",
  "value": "http://url.com/mylabel.jpeg",
  "packageId": "5q5f5q4zb"
}

```
*Label to be retrieved later*
```json
{
  "id": "LBL003", 
  "packageId": "5q5f5q4zb"
}
```
<!-- theme: warning -->

> ### Important
>
> If you provide a **Label to be retrieved later** it is necessary to subscribe to the [** label's callback**](https://woop.stoplight.io/docs/carrier/branches/english/docs/2.%20Basics/Subscriptions.md#callbacks) and to implement the [**Retrieving a label**](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1labels~1{labelId}/get) endpoint.

                        
                        
