---
title: "[SOLVED] Using Beej's Python flickrapi"
date: 2008-11-15
forum: Programming Talk
---

### Post by Tony Flury on 2008-11-15
I am trying to extend my knowledge of python by writing a flickr desktop client.

I am trying to use Beej's python flickrapi : [http://flickrapi.sourceforge.net/](http://flickrapi.sourceforge.net/)

and I am running into trouble at the first hurdle

1) I want my application to be able to handle multiple flickr users, but i can't see how once authenticated i can use the API to identify which flickr user has been authenticated.

2) the documentation itself seems to be far from complete, 
[http://flickrapi.sourceforge.net/apidoc/](http://flickrapi.sourceforge.net/apidoc/)

for instance an example is given of a class method of flickrapi.photosets_getList for retrieving a list of photo sets for a given user, but there is no such method documented.

If anyone has actually used this api and fathomed out the documentation please let me know.

---

### Post by Greyed on 2008-11-15
I have not touched the API so pardon my relative ignorance but have you tried the following in a Python interactive session:

```

import flickrapi
print flickrapi.photosets_getList.__doc__

```

---

### Post by Tony Flury on 2008-11-15
i am not sure why i did not think of that

It would appear that the documentation is correct, and the API does not contain the functionality i need for my application - which is a pain.

It seems to only contain the capabilities to upload and replace pictures, and not do all the other stuff i need it to do.

My python is ok but certainly not up to the point where i can contribute in any meaningful way to improving it.

---

### Post by Tony Flury on 2008-11-15
Ignore me - the flickrapi does something very clever and does not actually expose the API as class methods, so they are not listed under __dir__.

i now have to work out how to use the api :-)

Anyone with any clues would be appreciated.

---

### Post by Tony Flury on 2008-11-15
ok - I have two specific questions about the api - that i can't figure out

1) I can register to one acount - and it then seems to cache the Token for all time - how can i clear any cached token so i can register against a second acount

2) I want to provide the users with a meaningful name when they choose between the various accounts. I would like to actually use the Flickr account name - so how can i extract the name of the account i have authenticated against ?

---

### Post by Tony Flury on 2008-11-15
doh ! - was right in front of me ..

All you need to do is use the username function on the Constructor. These usernames can be anything - they don't have to be the same as the flickr account name.

---

