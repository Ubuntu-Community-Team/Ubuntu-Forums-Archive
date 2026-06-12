---
title: "problem with uodates"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by remeses on 2012-04-04
[B][SOLVED]
[/B]hi today i opened my terminal and wanted to uodate my ubuntu so i typed the following command
[B]sudo apt-get update
but i get error in terminal window
W : Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/B]
what does this mean

---

### Post by searchfgold6789 on 2012-04-04
It just means that it can't use the Ubuntu installation CD to get software. It doesn't need the CD anyway, so go to 'Software Sources", Ubuntu Software tab, and uncheck the Oneiric Ocelot CD-ROM.

---

### Post by osced on 2012-04-04
I would say it looks like they try to fetch information from cd-rom. I would say that something in your source list is telling it to update from your cd rom. Try to check your source list

---

### Post by kazztan0325 on 2012-04-04
It seems you need to invalidate a source: "cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/dists/oneiric/main/binary-i386/".

1. Open Dash, and type **Software Sources**.
2. Click on "Software Sources" icon, "Software Sources" window will appear.
3. Click on **'Ubuntu Software'** tab.
4. Tick OFF against an item: "cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/dists/oneiric/main/binary-i386/".
5. Click on 'Close' button.
6. Open up Terminal, and try again **sudo apt-get update**.

Hope this helps.

---

### Post by remeses on 2012-04-04
> **kazztan0325 said:**
> It seems you need to invalidate a source: "cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/dists/oneiric/main/binary-i386/".

1. Open Dash, and type **Software Sources**.
2. Click on "Software Sources" icon, "Software Sources" window will appear.
3. Click on **'Ubuntu Software'** tab.
4. Tick OFF against an item: "cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/dists/oneiric/main/binary-i386/".
5. Click on 'Close' button.
6. Open up Terminal, and try again **sudo apt-get update**.

Hope this helps.

thanlks man it is ok now

---

### Post by kazztan0325 on 2012-04-04
> **remeses said:**
> thanlks man it is ok now

You are welcome, remeses!

I'm glad to hear you have solved the problem.

Since your problem has solved, please edit your initial post and add a string **[SOLVED]** to the head of the subject.
Thank you.

---

