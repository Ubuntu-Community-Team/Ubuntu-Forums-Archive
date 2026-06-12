---
title: "GRIB trouble - libraries"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by leo_br_hidro on 2015-07-20
When trying to use GRIB_API, with this command:
```
leonardo@leoHP:~/builds/meteorological2$ grib_get -m -P shortName GF12051712

```
I received the following error:```
GRIB_API ERROR   :  Key/value not found
```



I  have found many sources on the meaning of keys in the GRIB message  standard. One of those sources actually shows that you can run grib  commands with the -f option, which would make it ignore errors. However,  the problem is that I have a compiled program that relies on GRIB, for  which I can't set that -f option.

---

