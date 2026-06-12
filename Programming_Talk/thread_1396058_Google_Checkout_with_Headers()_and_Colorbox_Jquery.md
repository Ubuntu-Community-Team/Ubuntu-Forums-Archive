---
title: "Google Checkout with Headers() and Colorbox Jquery Plugin"
date: 2010-02-01
forum: Programming Talk
---

### Post by Penteado on 2010-02-01
Hello everyone.


I render a cart inside the colorbox(jquery dialog plugin) iframe When the user clicks the google checkout button, i want to submit the form and show the result page(checkout) inside the colorbox plugin .
1st problem : 

```
<form method='post'target='_self' action='https://sandbox.google.com/checkout/api/checkout/v2/checkoutForm/Merchant/".$merchant_id."'>
```

This is the form tag, i tried to change the "target" attribute but it never shows up inside the iframe of the colorbox.

So i tried  a different method. 
Like this : 

```
<form method='post' id='googleform' target='_self' action='cart/cart-gateway-google.php'>
```

//cart-gateway-google.php
$```
host_path = "https://sandbox.google.com/checkout/api/checkout/v2/checkoutForm/Merchant/".$google_merchant_id;
$ch = curl_init ( $host_path );
$encoded = http_build_query ( $_POST );
curl_setopt ( $ch, CURLOPT_POSTFIELDS, $encoded );
curl_setopt ( $ch, CURLOPT_POST, 1 );
curl_exec ( $ch );
curl_close ( $ch );
```

Now the result page shows inside the colorbox iframe but with an error message 
"@ has sent Google a shopping cart with errors in it (...)."


With normal form post works fine but not inside the iframe :s


I would appreciate any help from more experienced developers.

Regards
Bruno

---

