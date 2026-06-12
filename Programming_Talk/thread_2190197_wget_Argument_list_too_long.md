---
title: "wget: Argument list too long"
date: 2013-11-26
forum: Programming Talk
---

### Post by veranyon on 2013-11-26
H! all
I have problem with downloading the big sites, have that one: [http://ubuntuforums.org/showthread.php?t=537797](http://ubuntuforums.org/showthread.php?t=537797) but have asks.

On that thread had give a hint: [COLOR=#000000]Uhm.. are you all crzy?[/COLOR]

[COLOR=#000000]just use "wget www.whatever.com/folder/{1..30}.html"

after it that one had been closed.

My problem:
[/COLOR]wget -E -c http://example.com/forum/viewtopic.php?t={12400..99980}
-bash: ...wget: Argument list too long

That example site have about 1700000 pages and I want to download it with concurrent wget process'. about 20 - 40 process.

How I can be made it?

Thanks.

---

### Post by Lars Noodén on 2013-11-26
wget would only be appropriate for small downloads.  Then you would use options like --no-parent --wait and others.  Take a look in the manual page for wget to find the others you would need.  

Again, wget is not good for bulk downloads.  Contact the site's maintainer and find out about alternate methods.  There may be a compressed tarball available or else an rsync option.

---

### Post by veranyon on 2013-11-26
got Offline Explorer (windows).
Thanks.
closed.

---

### Post by ofnuts on 2013-11-26
It is not very nice to the server to download a whole site like that.. you should spread the load over several days instead. A good server with bar you (or your IP) anyway if you use up too much traffic.

This said, with "wget -i" you can list the URLs in a file, which removes the problem of passing them as command parameters. A bonus of that method is that you can check the list against what you received (with big downloads, some pages are going to fail), and obtain a delta list that you can use for a second pass.. 

You can also have a script that calls wget on each URL (one wget instance per page download), which gives you a better control on the output, especially for URLs with parameters.

---

### Post by veranyon on 2013-11-26
[COLOR=#000000]1. I can change ip. Just reconnect pppoe one.[/COLOR]
[COLOR=#000000]2. have unlimited one.[/COLOR]
[COLOR=#000000]3. A site is forum with php one. Not clean html.[/COLOR]
4. there're over 1700000 pages without odd pages.
[COLOR=#000000]Just say what target I haunt:[/COLOR]
[COLOR=#000000]I want to find a some word on some site but without >over< 32 words and expressions. Google doesn't get that one, and I want to download all site and grep it.[/COLOR]

[COLOR=#000000]Excuse my English.[/COLOR]

---

