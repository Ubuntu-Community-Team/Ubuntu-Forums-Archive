---
title: "GNOME library reccomendation"
date: 2009-09-29
forum: Programming Talk
---

### Post by gnepets on 2009-09-29
Howdy Ubunteros,
I am looking to implement the get hot new stuff (GHNS) specification Located at.
[http://ghns.freedesktop.org/spec/](http://ghns.freedesktop.org/spec/)

it uses XML over HTTP (as I understand it) to pass the
-provider list (XML) (people who offer downloads).
-download metadata (XML)
and plain HTTP for
-payload (the download) (tar.gz or whatever)

so I am looking for GNOME-happy libraries that will help with the
-Downloading over HTTP
-Getting information from XML, validating conformance of XML



******
I have had a look so far on the GNOME developers area for libraries (libSoup maybe?), I am sure some of you here know more than me about developing on GNOME and could give some advice, any suggestions?

regards,
Stephen.

---

### Post by chrisjsmith on 2009-09-29
Not necessarily gnome/glib integrated, but:

libcurl - fetching
libxml - xml processing

They are both used inside gnome AFAIK anyway as the back end for most of the glib stuff.

---

### Post by gnepets on 2009-09-29
> **chrisjsmith said:**
> Not necessarily gnome/glib integrated, but:

libcurl - fetching
libxml - xml processing

They are both used inside gnome AFAIK anyway as the back end for most of the glib stuff.

haha,
this is good enough for me if I can't find something more GNOMEy, thank you, thank you.

regards,
Stephen.

---

