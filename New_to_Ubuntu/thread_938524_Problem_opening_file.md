---
title: "Problem opening file"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by nightfall47 on 2008-10-05
Alright, I've searched and tried things in similar scenarios, but nothing seems to work for me:(. I downloaded the Linux version of Owen Piette's wxSand from [http://www.piettes.com/fallingsandgame/download.html]("http://www.piettes.com/fallingsandgame/download.html"), and I can't seem to open it in any way. In properties, this is listed.

**Type:**      executable
**Size:**      2.9 MB (3025984 bytes)
**Location:**  /home/michael/Desktop
**Volume:**    unknown
**MIME type:** application/x-executable

I'd appreciate any help, as knowing how to open something this simple would only push me one step further into the world of Linux.

---

### Post by JoshuaRL on 2008-10-05
> **nightfall47 said:**
> Alright, I've searched and tried things in similar scenarios, but nothing seems to work for me:(. I downloaded the Linux version of Owen Piette's wxSand from [http://www.piettes.com/fallingsandgame/download.html]("http://www.piettes.com/fallingsandgame/download.html"), and I can't seem to open it in any way. In properties, this is listed.

**Type:**      executable
**Size:**      2.9 MB (3025984 bytes)
**Location:**  /home/---/Desktop
**Volume:**    unknown
**MIME type:** application/x-executable

I'd appreciate any help, as knowing how to open something this simple would only push me one step further into the world of Linux.

What does the Permissions tab say in the Properties dialog box?

---

### Post by nightfall47 on 2008-10-05
[img]http://i36.tinypic.com/11qlh6o.png[/img]


Is there any specific program type of thing I should choose to open the file with?

---

### Post by JoshuaRL on 2008-10-05
> **nightfall47 said:**
> [img]http://i36.tinypic.com/11qlh6o.png[/img]


Is there any specific program type of thing I should choose to open the file with?

Sorry man, I can't see that.  I think the dumb work filter cut it out.

---

### Post by nightfall47 on 2008-10-05
Owner:  michael
Access: Read and Write

Group:  michael
Access: Read-only

Others
Access: Read-only

Execute: [checked box] Allow executing file as program

SELinux context: unknown

---

### Post by JoshuaRL on 2008-10-05
Alright, you might want to change the access of group "michael" to read and wright.

But what type of file is it?  I can't look at that site right now (again, dumb filters) but what are the instructions there and what distro is it for?  Is it a deb?

---

### Post by nightfall47 on 2008-10-05
Well, it really doesn't say a file type. It just says "fsg-4.4 - Version 4.4 binary", and it also says "The linux executables requires GTK2." Is gtk2 manually installed? Or it is included in ubuntu?

---

### Post by marshal_mellow on 2008-10-05
open a terminal and type 
```
cd Desktop
./fsg-4.4

```

---

### Post by JoshuaRL on 2008-10-05
> **nightfall47 said:**
> Well, it really doesn't say a file type. It just says "fsg-4.4 - Version 4.4 binary", and it also says "The linux executables requires GTK2." Is gtk2 manually installed? Or it is included in ubuntu?

GTK2 is a toolset.  It is what Gnome (the desktop environment on regular Ubuntu) is based on.  So yes, you should have GTK2.  If it's a binary, then it needs to have the permissions changed, then run.  So do this:
```

cd ~/Desktop

```
The capital D is important, that takes you to your desktop.  (where I assume the file is.  If not, cd [change directory] to there instead)
```

sudo chmod 755 <file name>.bin

```
This will give it the permissions to run like it needs to.
```

<file name>.bin

```

See if that works.

---

### Post by nightfall47 on 2008-10-05
Ok, when I try what you said, JoshuaRL, it says this:
/home/michael/Desktop/fsg-4(2).4: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

marshal_mellow, when I try what you said to try, it says this:
bash: syntax error near unexpected token `2'

---

### Post by JoshuaRL on 2008-10-05
Alright, you'll need to search for that library to make sure you have it installed.  Do this:
```

apt-cache search libexpat

```

---

### Post by nightfall47 on 2008-10-05
This is the reply:

libexpat1 - XML parsing C library - runtime library
libexpat1-dev - XML parsing C library - development kit
libexpat-ocaml - ocaml expat bindings
libexpat-ocaml-dev - ocaml expat bindings
liblua5.1-expat-dev - libexpat development files for the lua language version 5.1
liblua5.1-expat0 - libexpat bindings for the lua language version 5.1
ser-jabber-module - contains the Jabber module (SIP-Jabber message translation)

---

### Post by JoshuaRL on 2008-10-05
> **nightfall47 said:**
> This is the reply:

libexpat1 - XML parsing C library - runtime library
libexpat1-dev - XML parsing C library - development kit
libexpat-ocaml - ocaml expat bindings
libexpat-ocaml-dev - ocaml expat bindings
liblua5.1-expat-dev - libexpat development files for the lua language version 5.1
liblua5.1-expat0 - libexpat bindings for the lua language version 5.1
ser-jabber-module - contains the Jabber module (SIP-Jabber message translation)

Alright, lets do a library grab and then see if that makes the binary run right.
```

sudo apt-get install libexpat1 libexpat-ocaml

```

---

### Post by nightfall47 on 2008-10-05
Alright, I tried that, then I tried what you suggested before, still to no avail. It gives me the same message :(

---

### Post by JoshuaRL on 2008-10-05
Alright, let's try the exact library it says is missing.
```

sudo apt-get install libexpat.so.0

```

---

### Post by nightfall47 on 2008-10-05
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libexpat.so.0

---

### Post by xreaper on 2008-10-05
hey, theres a slightly different way that I do it. all you have to do is make the file executeably from what I've read.

change the directory to where you saved it:

cd /home/XX/XX/XX

and then make it executeable:

chmod a+x ./<name of the file you downloaded here>

---

