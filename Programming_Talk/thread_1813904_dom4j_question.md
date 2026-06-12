---
title: "dom4j question"
date: 2011-07-28
forum: Programming Talk
---

### Post by jerry01 on 2011-07-28
I have an xml message which i need to parse. However attributeValue is the wrong thing to look for.

this is probably relatively basic but can someone who knows a bit about dom4j tell me how i can get the values for each field/node/element?


```
        <?xml version=\"1.0\" encoding=\"UTF-8\"?>
        <profileCheckoutRequest \">
        <merchantRefNum>12345</merchantRefNum>
        <param>
        <key>JSESSIONID</key>
        <value>12312311231</value>
        </param>
         <cancelUrl page=\"https://www.example.com/index.php/myaccounts/checkoutRequestFail\">
        <param>
        <key>JSESSIONID</key>
        <value>12312311231</value>
        </param>
        </cancelUrl>
        <paymentMethod>CC</paymentMethod>
        <currencyCode>USD</currencyCode>
        <shoppingCart>
        <description>Potash Shipment</description>
        <quantity>3</quantity>
        <amount>2500.00</amount>
        </shoppingCart>
        <ancillaryFees>
        <description>PST</description>
        <amount>200.00</amount>
        </ancillaryFees>
        <ancillaryFees>
        <description>GST</description>
        <amount>100.00</amount>
        </ancillaryFees>
        <totalAmount>2800.00</totalAmount>
        <customerProfile>
        <merchantCustomerId>joe.smith@yahoo.com</merchantCustomerId>
        <customerTokenId>12312211</customerTokenId>
        <isNewCustomer>false</isNewCustomer>
        </customerProfile>
        </profileCheckoutRequest>

```this is the code i have so far...

```
Document d = DocumentHelper.parseText(decodedMessage);
Element rootel = d.getRootElement();
Element el = (Element)rootel.selectSingleNode("merchantCustomerId");
fout.write( ("xml is: " + el.attributeValue("merchantCustomerId") + "\n").getBytes() );

```

---

### Post by myrtle1908 on 2011-07-28
Firstly, your XML is invalid.  Your root node is bogus ...

```
<profileCheckoutRequest \">
```

Secondly, merchantCustomerId is an element not an attribute so you cannot use attributeValue to obtain its value.

Have a look at the following example (untested but it should be fine) ...

```
<root>
 <thing id="1">
  <item>Something</item>
 </thing>
</root>

...
Element root = d.getRootElement();
Element thing = (Element)d.selectSingleNode("thing");
String thingId = thing.attributeValue("id"); // 1
Element item = (Element)thing.selectSingleNode("item");
String itemText = item.getText(); // Something
```

---

