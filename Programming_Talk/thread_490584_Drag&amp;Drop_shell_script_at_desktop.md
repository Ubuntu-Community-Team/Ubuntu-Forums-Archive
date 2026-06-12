---
title: "Drag&amp;Drop shell script at desktop"
date: 2007-07-02
forum: Programming Talk
---

### Post by Carlos Santiago on 2007-07-02
Hi,

I made a shell script that perform some operations on files that are passed as argument.

Now I would like to pass the argument by Drag&Dropping the file into the shell script icon, but the variable $1 don't show it.

Can anyone explain me how can I do it?

Thx

---

### Post by sabrewolf2006 on 2007-07-02
Not really suited to the programming forum but hey I'll bite..

If you're in GNOME you'll need something along the lines of this:
<script>  '%u' in a .desktop file to go on your panel

As an example I have included a .desktop file which sends files to my phone via bluetooth..

Hope this helps

P.S do bear in mind this will only take one file as an argument.. otherwise it will run two instances of the script..
(I get round this by having an alias in a terminal and then passing and then dragging multiple files on to that..)

---

### Post by Carlos Santiago on 2007-07-02
Thank you for the very quick answer :-D

I dont know why but with '%u' it didnt work, however it works with %f

I saw it reading other examples.

On gnome help I also saw different special codes, namely:
%f - run 1 time for each file dropped
%F - parse all files dropped (assumes that the program can handle them)
%u - run 1 time for each URL dropped
%U - parse all URLs dropped
among others!

The ubuntu help center actually gives important informations, really different from other OS :-D

Thanx again for your tip! ;-)

---

