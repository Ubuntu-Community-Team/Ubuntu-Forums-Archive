---
title: "my hot programming tip - use gzip when downloading pages"
date: 2009-01-25
forum: Programming Talk
---

### Post by NinjaWork on 2009-01-25
Geez man...I've been doing data mining for years. I once downloaded 30,000 pages in an afternoon.

AND, after all that time, I finally tried making a request using gzip. File size dropped from 19k to 4.5k and script speeded up from 2 secs to almost zero...I was amazed :p

---

### Post by slavik on 2009-01-25
could you give a bit more details on the command you used?

---

### Post by NinjaWork on 2009-01-25
> **slavik said:**
> could you give a bit more details on the command you used?

the key is adding to the http request:

```

Accept-Encoding: gzip

```

and, if you are using Perl:
```

use Compress::Zlib; 
$uncompressed = Compress::Zlib::memGunzip($data)

```

not all sites use gzip...for example the nytimes.com did, feedburner didn't

---

