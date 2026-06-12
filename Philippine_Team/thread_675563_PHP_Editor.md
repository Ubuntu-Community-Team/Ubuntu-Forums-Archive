---
title: "PHP Editor"
date: 2008-01-22
forum: Philippine Team
---

### Post by outkast08 on 2008-01-22
Hi, sa tingin ko meron naman mga Web Developers dito na marunong sa PHP. Just wanna ask what Application/s you use when you create web pages using PHP what PHP Editor would you suggest if you are in Ubuntu Environment.  I am exploring PHP and I am only using GEdit with syntax highligting for PHP Scripts. :)
Nag search na ko sa web tungkol dito at marami application akong nakita, sa tingin niyo maganda yung Eclipse? Anu ba katumbas ng Visual Studio na Linux App?

---

### Post by Samhain13 on 2008-01-23
Gedit lang ang gamit ko na may syntax highlighting tulad ng nabanggit mo.
Eclipse, hindi ko pa nasusubukan. :)

---

### Post by outkast08 on 2008-01-23
> **Samhain13 said:**
> Gedit lang ang gamit ko na may syntax highlighting tulad ng nabanggit mo.
Eclipse, hindi ko pa nasusubukan. :)

tnx.. GEdit din pala gamit mo. Try ko na lang Eclipse... tingnan ko kung ok naman siya.

---

### Post by nick.tux on 2008-01-25
okay din bluefish.

---

### Post by daxumaming on 2008-01-25
Im using Quanta, and I'm very pleased with it.
Haven't tried Eclipse though, I find it too sluggish

---

### Post by DiViDe on 2008-01-25
I'm using bluefish, ok naman.

> **daxumaming said:**
> Im using Quanta, and I'm very pleased with it.
Haven't tried Eclipse though, I find it too sluggish

try ko rin 'to baka sakaling maganda... hehehe thanks!

---

### Post by raxso on 2008-01-26
ako po still using the traditional vi editor.... hehehehehe old skul... :) pero sometimes  gedit

---

### Post by vrix on 2008-01-26
Dati, gedit din ang ginagamit ko, yun nga lang hindi ko madebug yung script medyo mano-mano pa, piniprint ko lang yung variables at nilalagyan ko nito: 

```
ini_set ('display_error',1);
error_reporting (E_ALL &~E_NOTICE); 
```

sa script. Ginamit ko na rin ang Quanta Plus at Gubed debugger. Ok naman pero may error messages na piniprint na hindi naman dapat. Ngayon, Eclipse Europa PDT ang ginagamit ko at debugger ko ay Xdebug pag web server, at Zend debugger pag internal scripts, mamili ka na lang.

Gumagamit din ako ng Netbeans version 6 pang PHP via plugin din tulad ng Eclipse. Nasa sa iyo na rin kung ano mas magugustuhan mo, kasi pag sa IDE, usually personal choice mo yun.

Punta ka sa blog na ito: [http://ooboontoo.blogspot.com](http://ooboontoo.blogspot.com) Title ay: How To Web Development in Linux September 2007.

:)

---

### Post by outkast08 on 2008-01-27
Yun! me mga debugger pala Eclipse at Quanta try ko dalawang to... saka pati na rin yung bluefish
Tnx sa mga suggestions niyo.... 
vi...:mrgreen: nano na lang o kaya emacs :lolflag:

---

### Post by headlessspider on 2008-01-30
eclipse is ok if you have plenty of memory. bluefish is pretty good also although parang tumigil sandali ng development...

---

### Post by ippiraman on 2008-02-01
I use geany on xfce. But any editor works for me.

---

### Post by .::welemski::. on 2008-02-02
Ang daming pagpipilian pare... depende sa taste and skills mo.

Quanta and Screem - ayos to pag purely html/css editing lang magaan then may code completion.

Vim/Emacs/Geany/GEdit/Pico ( text editor ) etc. - pag astig coder ka.


Tip lang : Real men use text editor ( emacs/vim/pico etc ), but real productive men uses IDE. kaya choose wisely :)

---

### Post by moodsey211 on 2009-07-09
I'm looking for a php editor with a ssh2 protocol bundled with it? Is there one?

---

### Post by gamels on 2009-07-10
akoo vi editor lang at text editor... i just make it simplier(for me the simplier the better)...

---

### Post by dsdeiz on 2009-07-10
vim user din dito.. Hehe

---

### Post by zeroseven0183 on 2009-07-10
I use **gedit** and/or **Screem**

---

### Post by daxumaming on 2009-07-10
> **moodsey211 said:**
> I'm looking for a php editor with a ssh2 protocol bundled with it? Is there one?

Quanta works well with fish:/, but I've recently dropped Quanta in favor of Netbeans and update server/production files via bzr or svn instead of copying, overwriting and editing files directly.

---

### Post by dodimar on 2009-07-10
Notepad2? (waaaa, spammer)...

I use , nano on Linux (nalilito ako sa vi, at console lang yung server, notepad2 pag nag eedit ako sa office, Windows kasi gamit dito)

> **daxumaming said:**
> Quanta works well with fish:/, but I've recently dropped Quanta in favor of Netbeans and update server/production files via bzr or svn instead of copying, overwriting and editing files directly.

boss dax, pano po gawin yun, hassle kasi minsan copy, everwrite, edit sa server files eh.

---

### Post by daxumaming on 2009-07-11
er... on Windows, you can install TortoiseSVN or TortoiseBZR to manage it. But you'll need a server if you choose Subversion. There's a free Subversion book out on the internet, so just Google it out. As for Bazaar, you can read the user manual: [http://doc.bazaar-vcs.org/latest/en/user-guide/index.html](http://doc.bazaar-vcs.org/latest/en/user-guide/index.html)

My workflow for Subversion is pretty simple. I create, edit, and delete files on my localhost. Commit them once I'm done. Login to my server, and issue the update command: *svn update* - and it'll update the files, including those that I've added and deleted.

As for Bazaar, I create, edit, or delete. Commit them when done. Push changes that I want logged to my bzr server. Login to my production server, and issue: *bzr pull bzr://sitename* to update my files. 

What I like about Bazaar is, I can push changes I only want to a publicly-accessible server while not worrying about those that I commit locally. e.g. ugly patches committed locally, and push them to a server once I'm done refining them. I can also bind it to a server if I feel like it, that way, it feels exactly like Subversion.

---

### Post by Samhain13 on 2009-07-12
> **daxumaming said:**
> My workflow for Subversion is pretty simple. I create, edit, and delete files on my localhost. Commit them once I'm done. Login to my server, and issue the update command: *svn update* - and it'll update the files, including those that I've added and deleted.

I take it this requires SVN to be installed on the remote host and you have shell access to it?

---

### Post by daxumaming on 2009-07-12
> **Samhain13 said:**
> I take it this requires SVN to be installed on the remote host and you have shell access to it?

Yes, but an svn server can be on another remote host - even your localhost. However, in order for this to be successful, you'll need shell access to the remote host itself.

---

### Post by dodimar on 2009-07-12
> **daxumaming said:**
> Yes, but an svn server can be on another remote host - even your localhost. However, in order for this to be successful, you'll need shell access to the remote host itself.

I don't have shell access on my current host. Still waiting for marlon's server though..

---

### Post by daxumaming on 2009-07-13
> **dodimar said:**
> I don't have shell access on my current host. Still waiting for marlon's server though..

Use Bazaar then, you can push your changes via FTP/SFTP or Samba. I haven't tried this setup though. Either way, you're versioning your codes - which is a '***must-do***' by all software developers.

---

### Post by dodimar on 2009-07-13
> **daxumaming said:**
> Use Bazaar then, you can push your changes via FTP/SFTP or Samba. I haven't tried this setup though. Either way, you're versioning your codes - which is a '***must-do***' by all software developers.

tnx boss.. will be reading Bazaar..

---

### Post by Samhain13 on 2009-07-13
> **daxumaming said:**
> Yes, but an svn server can be on another remote host - even your localhost. However, in order for this to be successful, you'll need shell access to the remote host itself.

Ngak, sayang. I don't have shell access to my remote host. This would have been a good mod on my workflow. I might take a look at Bazaar as well... or not. Bahala na si Batman. :(

---

### Post by outkast08 on 2009-07-16
Nabuhay pala ulit thread na to... :D Mejo matagal ko na rin d na vivisit Ubuntu forums. Hindi ko pa nagamit PHP sa professional work, ASP pa din kasi lahat project ko kaya most of the time MS Visual Studio gamit ko.

As of now I am using [[COLOR="Blue"]Eclipse PDT all-in-one from[/COLOR]]("http://www.zend.com/community/pdt?ecl=EclipseZend") zend when playing around with PHP codes in both windows and ubuntu environment.

---

### Post by Laibcoms on 2009-07-18
I use jEdit ^_^

Prior to that, I was using EmEditor under WINE.

---

### Post by creek23 on 2009-07-19
I use Geany.

[NetBeans+PHP]("http://www.netbeans.org/features/php/") module, pwede din.

---

### Post by pinoyskull on 2009-07-20
vim with custom vimrc, yung may syntax highlighting and line numbering :)

---

### Post by daxumaming on 2009-07-23
> **daxumaming said:**
> Use Bazaar then, you can push your changes via FTP/SFTP or Samba. I haven't tried this setup though.

Just tried this setup - I was wrong, it doesn't work. Pushed changes to a directory via FTP/SFTP or Samba would only set it up as a dumb server - it won't actually change your remote files to reflect the changes you've made.

Better use WinSCP (which works well on Wine) which would allow you to sync local and remote directories and files. And I still strongly suggest you use your preferred versioning tool.

---

### Post by businessgeeks on 2009-07-23
[Geany]("http://www.geany.org/") is a speedy little IDE for a lot of langauges.

[Komodo Edit]("http://www.activestate.com/komodo_edit/") is also good. I personally moved to this from geany but your mileage may vary.

---

### Post by djwisdom on 2009-07-24
[Aptana Studio]("http://www.aptana.com") is a good choice if your box is fast and you have sufficient GB of RAM
[Anjuta IDE]("http://www.anjuta.org") is another good candidate though your mileage may vary.
Don't forget the ubiquitous [VIM]("http://www.vim.org") and [Emacs]("http://www.gnu.org/software/emacs/").

Initially I used [Kate]("http://kate-editor.org/"), but lately since I'm into [LinuxMint]("http://www.linuxmint.org"), I'm exposed more to [gedit]("http://www.gedit.org").

---

### Post by diegoman on 2009-07-29
Personally, i use nano for creating and/or editing my basic PHP scripts, then i installed the LAMP package from tasksel to run the scripts

---

