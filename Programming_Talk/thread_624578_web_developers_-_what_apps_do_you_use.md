---
title: "web developers - what apps do you use?"
date: 2007-11-27
forum: Programming Talk
---

### Post by Jonne on 2007-11-27
I was just wondering which editors/ftp programs/ etc. fellow web developers use on Ubuntu to see if I can improve my workflow.

I use:

text editors:
 Geany (and sometimes scite and gedit)
Geany reminds me a lot of notepad++ on Windows, and the only thing lacking compared to N++ is a find-as-you-type search. I'd also love an editor that supports live editing of files, instead of having to upload manually.

ftp:
Filezilla:it's too bad the version in the repo's is a bit outdated. Drag and drop to and from anywhere would be nice. For that reason I sometimes just use Nautilus instead.

So, what do you guys use, and why?

---

### Post by smartbei on 2007-11-27
Geany almost exclusively, and GEdit when I need Hebrew support (Geany has a tendancy to crash messily during certain operations on Hebrew (and therefore probably most non-english characters) text.

For ftp I use the FireFTP extension for FireFox, though it is a bit underpowered for my use (I'm looking for a different one).

---

### Post by kretara on 2007-11-27
I do 90% of my web development in OS X, so I'll start there.

OS X
BBEdit for all editing, Terminal for command line stuff and Fugu for SFTP/SCP.  

Linux/Ubuntu
GEdit and nano for editing.  SCP and FireFTP for file movement.

Windows
UltraEdit for editing and WinSCP/FireFTP for file movement.

---

### Post by MicahCarrick on 2007-11-27
I'm a professional web developer working in GNOME. I wrote a writeup on some of the tools you can use: _[Web Development in Linux (GNOME)]("http://www.micahcarrick.com/09-28-2007/web-development-linux.html")_. 

Firefox has some VERY handy extensions for the web developer. I use the Web Developer extension, the validator extension with SGML parser, Source Chart extension, and Firebug. Firebug is REALLY handy for debugging CSS layouts since you can change things on the fly in Firefox with it.

I also spend a lot of time on the command line. If you don't have SSH access on your host, you should request it. It really can help. Furthermore, you can mount your SSH connection in gnome and work in it using Nataulis just like any other folder. 

For FTP, I just use gFTP as I don't need to use FTP too often. SSH takes care of most of those needs (without having to worry about xfering images in binary mode and scripts in ascii mode).

And if you're host supports MySQL remote logins or if you are setting up your test environment locally, the MySQL GUI tools come in handy (unless you prefer phpMyAdmin). 

For my editor, I use Gedit as described on _[Customizing gedit as a Web Developer’s IDE]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html")_. I prefer it for it's light-weight, stability, simplicity, and plugin system. I have everything I need (remote file editing, syntax highlighting, snippets, symbol browser, etc.) without the clutter of some of the more feature-rich IDEs.

Some of the editors/IDEs to look at are Geany, Bluefish, Quanta, Aptana, Eclipse, gPHPEdit, Screem, Kompozer, and Amaya.

---

### Post by kretara on 2007-11-27
> **MicahCarrick said:**
> 
Firefox has some VERY handy extensions for the web developer. I use the Web Developer extension, the validator extension with SGML parser, Source Chart extension, and Firebug. Firebug is REALLY handy for debugging CSS layouts since you can change things on the fly in Firefox with it.

Thanks for mentioning the tools that Firefox has.  
They have become so second nature to me that I no longer think of them at all, I just use them.

---

### Post by Jonne on 2007-11-27
> **kretara said:**
> Thanks for mentioning the tools that Firefox has.  
They have become so second nature to me that I no longer think of them at all, I just use them.
Seconded, i didn't even think of including the essential Firefox extensions because i assumed everyone was already using them ;).

I also run apache/php/MySQL locally, since it's pretty convenient to have a testing environment on your HD.

You probably all are using VMWare and/or Virtualbox to test IE too?

---

### Post by MicahCarrick on 2007-11-27
> You probably all are using VMWare and/or Virtualbox to test IE too?

Oh right! I use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") to test in IE 5.5 and 6 (although IE 5.5 users have dropped below 2% on the main site I work on). IE7 is coming soon, well, it's working but not yet rock solid.

I also test in Konqueror which uses a similar rendering engine as Safari which helps me find javascript problems that come up in Safari. 

Basically, I code for Firefox and standards, testing in IE all the while to make sure those 2 work. If IE and Firefox are working, chances are the other ones are too. But, I also test in Konqueror and Opera before deployment. (Actually, I jump on a windows and mac machine before important deployments, but as far a Linux goes, those pretty much do the trick).

---

### Post by Jonne on 2007-11-27
> **MicahCarrick said:**
> I also test in Konqueror which uses a similar rendering engine as Safari which helps me find javascript problems that come up in Safari. 
I've noticed that Safari has some different bugs than Konqueror, so you'll always need to test on Safari too (at least until the first stable webkit browser comes back to Linux).

---

### Post by ICEcoffee on 2007-11-27
To test IE in Linux, cant you just download and install the ietabs extension? I'm not sure which versions it renders for, but I would have thought that would be a convenient method?

---

### Post by Kadrus on 2007-11-27
> **kretara said:**
> I do 90% of my web development in OS X, so I'll start there.

OS X
BBEdit for all editing, Terminal for command line stuff and Fugu for SFTP/SCP.  

Linux/Ubuntu
GEdit and nano for editing.  SCP and FireFTP for file movement.

Windows
UltraEdit for editing and WinSCP/FireFTP for file movement.

Do you use CODA?...It is pretty good..
[http://www.panic.com/coda/](http://www.panic.com/coda/)

---

### Post by kretara on 2007-11-27
> **Kadrus said:**
> Do you use CODA?...It is pretty good..
[http://www.panic.com/coda/](http://www.panic.com/coda/)

After 8 years as a full time Web Developer, I moved into an Analyst position, so my web work is a shadow of its former self.
If I was still doing web full time, CODA would be one of my main tools.  I have used it a few times and it is an excellent product.  Although I still believe that BBEdit is one of the best editors available.

---

### Post by Jonne on 2007-11-27
> **ICEcoffee said:**
> To test IE in Linux, cant you just download and install the ietabs extension? I'm not sure which versions it renders for, but I would have thought that would be a convenient method?
No, IETab only works on Windows (it basically loads the library IE uses to load a website in a FF tab). To run IE on Linux you either need a virtual windows or WINE (ie4Linux).

---

### Post by tyrion2323 on 2007-12-05
Hi Everyone,

I am not a web-developer; however, my brother is.  I am planning to build him a desktop (he uses a MacBook Pro) for his office, and I wanted to install Kubuntu.

I know he uses Coda on his Mac as his primary tool, and being the layman that I am, I am really unfit to judge what Linux has to offer as a substitute.

Any help would be greatly appreciated!

Thanks,

/jacob

---

### Post by Jonne on 2007-12-05
I don't think anything on Linux fits that niche (especially not with all the effects coda has), although i might be wrong about that. The Linux way is to use seperate apps that do one thing well instead. But if you have sftp access to the server, you can just browse through the remote files in nautilus, and edit your files live in gedit, and the same is probably true for the equivalent kde apps (Konqueror & Kate).

For previewing I prefer a real browser (have firefox with reloadevery run on a desktop). Don't force him to use Linux if he doesn't want to, though.

---

### Post by ThinkBuntu on 2007-12-05
I'm on a Mac, but if you ever adopt this web design dream machine I think my advice could be useful:

FTP: Transmit - Nothing comes close
Graphics: Photoshop and Illustrator (99% photoshop, although I want to learn to make comps in Illustrator)
Code: TextMate, moving to Vim. Only a matter of time. But TextMate is very good and has won a number of Emacs and Vim converts. Far superior to BBedit
Time: On The Job
Browser testing: Firefox 2, Opera 9, Safari 3, Parallels running Windows with: Internet Explorer 6 & 7, Opera 9, Firefox 2

That's about it. Using TextMate and Transmit is very very quick.

---

### Post by pmasiar on 2007-12-05
Google is your friend, gives links like: [http://www.micahcarrick.com/09-28-2007/web-development-linux.html](http://www.micahcarrick.com/09-28-2007/web-development-linux.html)

---

### Post by tyrion2323 on 2007-12-05
Hey Guys, thanks for the responses!  I appreciate them - again, as someone with extremely limited experience in web-design, the majority of what you've said is a little lost on me, but I'm learning!

"Don't force him to use Linux if he doesn't want to, though."

I'd buy him a Mac if I had more than $300 to spend!  :)

---

### Post by ThinkBuntu on 2007-12-05
> **tyrion2323 said:**
> Hey Guys, thanks for the responses!  I appreciate them - again, as someone with extremely limited experience in web-design, the majority of what you've said is a little lost on me, but I'm learning!

"Don't force him to use Linux if he doesn't want to, though."

I'd buy him a Mac if I had more than $300 to spend!  :)
Used? Payments? etc. Just a thought.

---

### Post by zach12 on 2007-12-05
Bluefish

and gftp

---

### Post by khughitt on 2008-05-29
mysql-query-browser and mysql-admin are also useful for working with MySQL databases.

---

### Post by altonbr on 2008-06-06
[LIST]
[*]Firefox (Web Developer, Firebug)
[*]gEdit (over SSH and FTP)
[*]Nautilus (for SSH and FTP)
[*]Adobe Photoshop CS2 in Wine for graphics
[*]BASH (vim and ssh) when I need it.
[*]KohanaPHP (PHP Framework)
[/LIST]

Looking into:
[LIST]
[*]Geany
[*]gPHPEdit
[/LIST]

Macintosh:
[LIST]
[*]TextMate
[/LIST]

I also run a localhost on my Ubutnu machine, which can be installed like this:
```
sudo aptitude install apache2 php5 mysql-server phpmyadmin && sudo rm /var/www && mkdir $HOME/localhost && sudo ln -s /var/www $HOME/localhost && ln -s /usr/share/phpmyadmin $HOME/localhost/admin
```

This essentially creates a localhost on your desktop computer, makes the root of your localhost /home/<$username>/localhost, sets up [http://localhost/admin](http://localhost/admin) for phpmyadmin and of course install MySQL and PHP5.

Enjoy and good luck!

---

### Post by Kadrus on 2008-06-06
Firefox,Gedit,LAMP(+perl),Ocisgen(Eliom)..GIMP for images/design..etc..

---

### Post by pelle.k on 2009-11-16
The gimp is great for web design. I miss that on OS X. Sure i could use the X11 gimp, but i prefer to stay native. Pixelmator doesn't have paths yet, and that is a must for me. Photoshop is out of the question, since it's expensive, not written in cocoa, and bloated (although i'm sure it's a great tool).
For local web development, i use MAMP, period. It's a great app.
Still trying out text editors. Coda is great, but it's primarily a webdev editor. I prefer to use/learn one editor well, and use that for all kind of jobs. BBedit is super expensive, and the interface is outdated. Texwrangler lacks auto-completion and call tips. Textmate is wierd with the project tab/drawer managment - i cant just drop files in the interface unless i create a project first. I really miss geany!
I'm thinking i will buy forklift ftp client as well. Looks just as nice as transmit.

On ubuntu i use
[LIST]
[*]geany (although bluefish is nice too)
[*]lighttpd/php/mysql
[*]the gimp
[/LIST]
LOL, that's about it. I super happy with these three tools. I Wish i could use them everywhere!

---

### Post by Sacker on 2009-11-16
I use

Eclipse with Pydev - I use django mostly.
Gedit or kate depending on whatever one Im using at the moment.
Gimp

Firebug

---

