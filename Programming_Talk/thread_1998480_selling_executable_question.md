---
title: "selling executable question"
date: 2012-06-06
forum: Programming Talk
---

### Post by nolag on 2012-06-06
I'm not 100% sure if this is the right place to post this question, sorry ahead of time if it's in the wrong place.  

I have my executable and a dll.  The dll is compiled from code under MIT.  I know that I can sell them, but where must I present the MIT license?  Is a read me saying the library is under MIT good enough, or does my app need to say "hey I use a library under MIT".  It is dynamically linked.  Any references to back up what you think would be greatly appreciated :D.  I have not modified the MIT library in any way, and am willing to put in the read me where they can get it.

---

### Post by roelforg on 2012-06-07
May i note that dll is a windows term? Linux users prefer shared library (though, technically, dll's ok).
Second: Some people here (me included) don't like threads that have to do with selling apps, so use a good and descriptive subject next time, mkay?
 
To answer the question:
As long as the shared lib is provided seperatly (example: cclive & libquvi), you can distribute the binary using any licence you wish. Just as long as the shared lib is provided under it's MIT licence.

---

### Post by nolag on 2012-06-12
> **roelforg said:**
> May i note that dll is a windows term? Linux users prefer shared library (though, technically, dll's ok).
Second: Some people here (me included) don't like threads that have to do with selling apps, so use a good and descriptive subject next time, mkay?
 
To answer the question:
As long as the shared lib is provided seperatly (example: cclive & libquvi), you can distribute the binary using any licence you wish. Just as long as the shared lib is provided under it's MIT licence.

Is a library not saved as dll if it's in mono?  Yeah I know some people don't like threads about selling apps, but I am being honest about my intent.  Thank you for your reply and thanks for getting back to me (I have been busy just read this now).

I am mostly concerned about how I keep the library I reference under MIT, so like can I just include a text file that says "file A is under MIT" and includes the license or do I need to say somewhere in my app's about that it references them and what license it is under?  Also, do you have anything I can reference for this (I trust you, but I just don't understand exactly the wording like a lawyer and I am talking with people who do).

Thanks again, I appreciate your help!

---

### Post by josephmills on 2012-06-12
all upstream code needs to have a copy of any licence that they use. 
also when you are builing you app and you go to alter the debian/copywrite info you will need to include all your info there also but as long as the "Upstream" <orig.tar.gz> has all the stuff then you are all good you do not need to push a copy of licence to user if you do not want unless stated in original upstream licence but if you do the correct place to put them is 
```
/usr/share/common-licenses/<licence>
```

and also in 
```
/usr/share/doc/<name-of-app>
```

Now the debian/copyright file looks like this 
```
 
Format: http://dep.debian.net/deps/dep5
Upstream-Name: snmpcheck
Source: <url://example.com>

Files: *
Copyright: <years> <put author's name and email here>
           <years> <likewise for another author>
License: GPL-3.0+

Files: debian/*
Copyright: 2012 Joseph Mills <XXXXXXXXXX@myemail.com>
License: GPL-3.0+

License: GPL-3.0+
 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.
 .
 This package is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.
 .
 You should have received a copy of the GNU General Public License
 along with this program. If not, see <http://www.gnu.org/licenses/>.
 .
 On Debian systems, the complete text of the GNU General
 Public License version 3 can be found in "/usr/share/common-licenses/GPL-3".

[COLOR="Blue"]# Please also look if there are files or directories which have a
# different copyright/license attached and list them here.[/COLOR]

```



look at this part 
```
Format: http://dep.debian.net/deps/dep5
Upstream-Name: snmpcheck
[COLOR="green"]Source: <url://example.com>
[/COLOR]
```
```
[COLOR="red"]Files: *
Copyright: <years> <put author's name and email here>
           <years> <likewise for another author>
License: GPL-3.0+[/COLOR]
```

```
[COLOR="orange"]Files: debian/*
Copyright: 2012 Joseph Mills <XXXXXXXXX@myemail.com>
License: GPL-3.0+[/COLOR]
```


[COLOR="green"]Notice that I have to declare all upstream links of code [/COLOR]

[COLOR="red"]
This part I must list all other people's work and all of there licences that they are using 

notice how I can even get down to a single file  
Files: /src/somemit.pl
Copyright: <years> <put author's name and email here>[/COLOR]




[COLOR="orange"]Now to copyright all my files that I have made 
[/COLOR]
then add the rest 
[COLOR="Blue"]# Please also look if there are files or directories which have a
# different copyright/license attached and list them here.[/COLOR]
If you would like to learn more about this I suggest reading the debian maintainers guide \

hope that this helps



Ps I tink that it is awesome That you want to sell app. 
make sure you put it on [https://apps.ubuntu.com/cat/](https://apps.ubuntu.com/cat/)

good luck 
:)

---

### Post by nolag on 2012-06-13
Thank you for the help.  I am actually working with a mono library under MIT, but I am sure it will be similar for me :).

---

