---
title: "Writing an eCAP plugin for Squid: How to link OpenSSL and other libraries"
date: 2014-05-28
forum: Packaging and Compiling Programs
---

### Post by Pasquale_Puzio on 2014-05-28
[SIZE=3][FONT=arial][COLOR=#333333]Hi all,

I'm writing an eCAP adapter (in C++) for Squid. I've seen that libtool is required in order to create a library and import it into Squid.[/COLOR]
[COLOR=#333333]
I started from the adapter_modifying example (that can be found here [http://www.measurement-factory.com/tmp/ecap/ecap_adapter_sample-0.2.0.tar.gz](http://www.measurement-factory.com/tmp/ecap/ecap_adapter_sample-0.2.0.tar.gz)) and added some features (encryption of JSON objects).[/COLOR]
[COLOR=#333333]In order to do so, I'm using this library [https://code.google.com/p/rapidjson/](https://code.google.com/p/rapidjson/) and this OpenSSL wrapper [https://github.com/shanet/Crypto-Example](https://github.com/shanet/Crypto-Example)[/COLOR]
[COLOR=#333333]
After compiling and installing the adapter (it involves the creation of a library with libtool), I've run squid but the adapter crashes as soon as I instanciate an object of the OpenSSL wrapper.[/COLOR]
[COLOR=#333333]My plugin stops running as soon as I instantiate the Crypto wrapper:[/COLOR]
Crypto crypto;
[COLOR=#333333]
If I don't execute the adaptation method and just buffer and forward the chunks, everything works fine. Do you see anything in the code of this library [https://github.com/shanet/Crypto-Example](https://github.com/shanet/Crypto-Example) that may cause this issue?[/COLOR]
[COLOR=#333333]
Do you know how I can access the error log (or standard error) of my plugin? How can I correctly link these two libraries to my adapter? Which commands should I execute?[/COLOR]
[COLOR=#333333]
Thanks[/COLOR][/FONT][/SIZE]

---

