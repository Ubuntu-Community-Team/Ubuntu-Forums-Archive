---
title: "cURL php"
date: 2010-05-29
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-05-29
I am curl'ing a webpage in php, but I only need the first little bit of the webpage, so is there a way to limit how much of the page is loaded?  I would like to try this to see if it will improve the speed of the page that is curl'ing the other page, since at the moment it is adding about 1.5 seconds to the page load.

---

### Post by januzi on 2010-05-30
curl_setopt($ch, CURLOPT_RANGE, '0-500');
and maybe CURLOPT_RETURNTRANSFER

At the stackoverflow I found something about CURLOPT_WRITEFUNCTION:
```

// php 5.3+ only
// use function writefn($ch, $chunk) { ... } for earlier versions
$writefn = function($ch, $chunk) { 
  static $data='';
  static $limit = 500; // 500 bytes, it's only a test

  $len = strlen($data) + strlen($chunk);
  if ($len >= $limit ) {
    $data .= substr($chunk, 0, $limit-strlen($data));
    echo strlen($data) , ' ', $data;
    return -1;
  }

  $data .= $chunk;
  return strlen($chunk);
};

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://www.php.net/');
curl_setopt($ch, CURLOPT_RANGE, '0-500');
curl_setopt($ch, CURLOPT_BINARYTRANSFER, 1);
curl_setopt($ch, CURLOPT_WRITEFUNCTION, $writefn);
$result = curl_exec($ch);
curl_close($ch);

```

---

### Post by Finalfantasykid on 2010-05-30
Thanks that did exactly what I wanted.  It went from taking 1.5 (extra) seconds to load, down to about 0.6.

---

### Post by januzi on 2010-05-30
You could also use AJAX. Document is ready, so You fire up get_the_data_by_curl function and just wait for the data.

---

