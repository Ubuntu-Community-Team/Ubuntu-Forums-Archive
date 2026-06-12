---
title: "HOWTO: Latest OpenOffice 2 Beta with Ubuntu Linux"
date: 2005-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by sebgate20 on 2005-04-30
As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.

This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

Leave any comments here or email me directly at [email]spayne@evolutioncolt.com[/email]. Could a Moderator make this thread a sticky?

Seb Payne
Systems Administrator - Evolution Colt

---

### Post by thechitowncubs on 2005-04-30
[QUOTE=sebgate20]As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.

This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

Leave any comments here or email me directly at [email]spayne@evolutioncolt.com[/email]. Could a Moderator make this thread a sticky?

Seb Payne
Systems Administrator - Evolution Colt[/QUOTE]
 Nice HOWTO!

---

### Post by i3dmaster on 2005-05-01
[QUOTE=thechitowncubs]Nice HOWTO![/QUOTE]

Nice, thanks!

---

### Post by Seth on 2005-05-01
That's not a good method at all. Why not just use the debs?

[http://ftp.linux.cz/pub/localizatio....org/devel/680/](http://ftp.linux.cz/pub/localizatio....org/devel/680/)

m97 is even there.

---

### Post by thechitowncubs on 2005-05-01
worked great for me =D

---

### Post by sebgate20 on 2005-05-01
I was not aware of the Debian Packages produced there but I think that my HOWTO still has some relevance! OpenOffice 2 Releases are only made as RPMs so he must convert them to Debian Packages. The only thing my HOWTO covers is making the GNOME menu links and installing the actual icons!

Seb

---

### Post by Heliode on 2005-05-01
Thanks for the great howto! The package I got with apt was hopelessly outdated, plus the interface on this one looks better.

However, do you know how I could get dutch spell checking working? It worked with OOo2 that I got from debs, maybe copy something somewhere?

And by the way, I could copy/paste most of the commands on your page right into a terminal but you forgot a couple of 'sudo'; with the chmod and the copying of the icons. 

Other than that, great tip! Thanks!

Edit: Ok I figured it out;

Fist, get the Myspell package for your language. For me, that was [myspell-nl](http://www.ubuntulinux.org/wiki/UbuntuNederlandsEr). 

Now, do this;

```

cd /opt/openoffice.org1.9.95/share/dict/ooo
sudo cp /usr/share/myspell/dicts/nl* .    #or where nl is your language
sudo gedit dictionary.lst

```

now you'll have to add something like the following lines to the dictionary.lst file;

```

DICT nl NL nl_NL

```

Now, start OOo2 again, and go to tools -> options -> language settings -> languages, and select dutch (or whatever language) there. 

Hope this helps!

Maybe you could add this to your page?

---

### Post by sebgate20 on 2005-05-01
I've just written a bash script that automates the whole process. It downloads the files, unzippes them, converts them to Debian Packages, installs them, makes the menu links, installs the icons and set the file permissions.

I will notify all when it is finished. Probally in an hour or two!

Seb

---

### Post by Karlos on 2005-05-01
not being funny but I installed OO2 from universe the other day

it was easy

use synaptic


EDIT: ok didnt realise it was a more up to date version

ignore the above rant

I was wrong....as usual....ask my missus she'll tell yer..!

---

### Post by Psquared on 2005-05-01
[QUOTE=sebgate20]I've just written a bash script that automates the whole process. It downloads the files, unzippes them, converts them to Debian Packages, installs them, makes the menu links, installs the icons and set the file permissions.

I will notify all when it is finished. Probally in an hour or two!

Seb[/QUOTE]

That would be cool -- will it work for Warty??

---

### Post by sebgate20 on 2005-05-01
OK! Here is the script. I've tested it as much as I can but it is down to you now. Test and Leave feedback!

You can download the script from: [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh)

I recommend you run it something like this (in a terminal):

cd ~
wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh)
sh evolutioncolt_oo2.sh

And just watch it go! As I said, it does everything listed in the HOWTO so you only have to enter your password for the sudo commands. It should work with Warty but give it a go and report back.

Seb

---

### Post by Shadar on 2005-05-01
Just a small problem with the icons. The file is missing from your server?

```
wget http://www.evolutioncolt.com/downloads/EvolutionColt_OO2.tar.gz
--15:22:29--  http://www.evolutioncolt.com/downloads/EvolutionColt_OO2.tar.gz
           => `EvolutionColt_OO2.tar.gz'
Resolving www.evolutioncolt.com... 195.137.120.148
Connecting to www.evolutioncolt.com[195.137.120.148]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:22:30 ERROR 404: Not Found.
```

---

### Post by sebgate20 on 2005-05-01
If you read the script, you will find the file has been renamed to EvolutionColt_OO2-0.0.3.tar.gz.

I would encourage you to use the script!

Seb

---

### Post by sebgate20 on 2005-05-01
I've updated the page on the Evolution Colt website for the new file for those who want to install it manually.

The instructions for using the automatic script can also be found here. The page is at [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

Thanks again for your comments  :) 

Seb

---

### Post by ZC3rr0r on 2005-05-01
Thanx alot for the great install script! I hope this will run a lot faster than the OpenOffice supplied with Ubuntu Hoary.

---

### Post by sebgate20 on 2005-05-01
Thanks to the folk on #ubuntu, I've had to make two scripts, one to install the Sun Java Runtime and other assumes you already have it installed.

If you already have OpenOffice.org 2 Beta installed and need to Java Runtime, you can find instructions at [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) on how to install it. You will find there are two scripts on the server:

a.) evolutioncolt_oo2_java.sh (the Java version)
b.) evolutioncolt_oo2.sh (the non-Java version)

You can find the updated guide at [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php).

Cheers

Seb

(It is OpenOffice.org 2 Base that requires the JRE FYI)

---

### Post by derrick1985 on 2005-05-01
Openoffice installed successfully, but the icons/menu's didn't copy over correctly. I had to add them manually (just copy over the files)

Thanks a lot, worked out great (except for the stupid icons)

---

### Post by sebgate20 on 2005-05-01
What do you mean 'didn't copy over'? Did you run the script? If so, what was the error?

Thanks

Seb

---

### Post by und3rdog on 2005-05-01
Good install method, after I figured out to replace 00 with OO everthing went smooth.  I was too late last night to try out the script sorry, but good write up all the same. OO2 is definately worth it, for all those wondering out there.  Mad, Crazy updates to the interface ( comparable to the 2000 -> XP upgrade of another nameless office suite).  If you have the time give it a shot.

-Luke

---

### Post by sebgate20 on 2005-05-01
Can you tell me where you had to replace 00 with OO? I'll update the script then but I found that it worked fine as it is!

Seb

---

### Post by popdog on 2005-05-01
[QUOTE=derrick1985]Openoffice installed successfully, but the icons/menu's didn't copy over correctly. I had to add them manually (just copy over the files)

Thanks a lot, worked out great (except for the stupid icons)[/QUOTE]

Same problem here, unfortunatly i closed the terminal before copying down the error.  I found the icons and menu items in the archive, where do I copy them to?

---

### Post by ZC3rr0r on 2005-05-01
Okay,OpenOffice looks great, but I had to modify the script a little. For some reason the untarring pointed to the tar itself instead of the relative path, so the script exited there. Little modifications made it working fine though.

---

### Post by derrick1985 on 2005-05-01
[QUOTE=sebgate20]What do you mean 'didn't copy over'? Did you run the script? If so, what was the error?

Thanks

Seb[/QUOTE]

Sorry, I don't have the error anymore.

What I did was I made a directory called oo2 in my home directory and wgot the file and ran it from there. The error was that it couldn't find the files to copy over.

---

### Post by kperkins on 2005-05-01
I'm getting an error 
Details: Failed to execute child process "/opt/openoffice.org1.9.95/program/soffice" (No such file or directory)
openoffice won't launch.
Help

edit--and no, soffice _is_ not there.

---

### Post by Karlos on 2005-05-01
same here

failed to execute bla......

---

### Post by alphazero on 2005-05-01
It worked great for me. I just edited the menus as:
soffice -writer (and so forth)

instead of:
/opt/openoffice.org1.9.95/program/soffice -writer

That way any future beta versions will work without complications.

---

### Post by kperkins on 2005-05-01
Well my problem is that soffice isn't anywhere on my system.   ](*,)

---

### Post by kperkins on 2005-05-01
I figured it out.  I had a bad download on the OOo*.tar.gz download, and everything didn't get included in the .debs when  the rpms got aliened (ie. all the rpms weren't there.)
Trying a reinstall now.

---

### Post by Simian on 2005-05-01
Thanks sebgate20,

That's a lot better than the one that I picked up on apt. The spellchecker works with this one.

---

### Post by sebgate20 on 2005-05-02
Glad I can help  :) 

I've updated the script again so it works properly. I'm thinking of putting OpenOffice.org 2 Beta onto CD-ROM so those without Broadband can take advantage of the new version.

Seb

---

### Post by abmcr on 2005-05-02
The script work fine: thank you. At the urlhttp://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m95/; i want to install my language pack but the sh script don't work: anyone know how i fond a only rpm package to convert with alien? Thank you (please excuse my english language) Ciao

Andrea - Italia

---

### Post by raven on 2005-05-02
[QUOTE=kperkins]I'm getting an error 
Details: Failed to execute child process "/opt/openoffice.org1.9.95/program/soffice" (No such file or directory)
openoffice won't launch.
Help

edit--and no, soffice _is_ not there.[/QUOTE]


[QUOTE=Karlos]same here

failed to execute bla......[/QUOTE]


It's not a silver bullet but I think what happen to you, is *.deb files
could not be installed cause the dpkg area was locked by synaptic
(it's possible that it was open when you tried to execute the script)
if you look at the terminal message you could maybe
see this and that is why you do not have soffice.  :smile:

---

### Post by abmcr on 2005-05-02
For the italians users: at [this URL](http://abmcr.altervista.org/openofficeorg-it_1.9.95-2_i386.deb) you find the debian package for translate the OO version installed with the script.

---

### Post by abmcr on 2005-05-02
The correct URL is
[http://abmcr.altervista.org/openofficeorg-it_1.9.95-2_i386.deb](http://abmcr.altervista.org/openofficeorg-it_1.9.95-2_i386.deb)

It is needeb to copy and then paste the URL in the browserlink.

---

### Post by slipp3dstr3am on 2005-05-02
well so far so good...

i'm generating the deb files now ... no problems as of yet

---

### Post by AndyAWS on 2005-05-02
One question before I try this...

Should I uninstall OO1.1.3 beforehand...or does this install along side OO1.1.3...or will this update it?

---

### Post by N'Jal on 2005-05-02
1.1.3 are a sperate package 2beta will install happily alongside it. From the repo's that is. I havn't managed to get this to work for some reason

---

### Post by Karlos on 2005-05-03
i just re-done the whole thing and it all works fine...cheers

---

### Post by dilerra on 2005-05-03
I used your script and everything worked like a charm.

Just wanted to share my experience of how to customize OO with a custom languagepack (swedish in my case).

1. Download an appropriate languagepack at:
[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m95/](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m95/)

2. Open a terminal and go to the directory where you downloaded the file.

3. Enter the following command:
tail -n +146 OOo_1.9.95_LinuxIntel_langpack_sv.sh > langpack.rpm

4. Next, convert the rpm-file to deb-format:
sudo alien -k langpack.rpm

5. Finally, install the deb-package:
sudo dpkg -i openofficeorg-sv_1.9.95-1_i386.deb

Now you're done! Of course, the files COULD (and probably will =)) have other names on your system. Just start OpenOffice and everything should now be in "your" language =)

Good luck!

---

### Post by rhys on 2005-05-03
[QUOTE=sebgate20]As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.

This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

Leave any comments here or email me directly at [email]spayne@evolutioncolt.com[/email]. Could a Moderator make this thread a sticky?

Seb Payne
Systems Administrator - Evolution Colt[/QUOTE]
 I just wanted to say that I am using OO2, installed by the Seb's script, beautifully. I am so overjoyed to not have to look at the disgusting OO1 interface anymore. :)

Peace from rhys.

---

### Post by sebgate20 on 2005-05-03
Thanks :smile: 

I'm glad I can help. Expect to see a lot more of the this sort of thing coming from Evolution Colt very soon. Our aim is to help and bring Linux to the desktop soon.....

Seb

---

### Post by sebgate20 on 2005-05-03
You may also like our Beagle tutorial at [http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall) which was also written by me. It is step by step for the latest verion of Mono 1.1.6 and Beagle 0.0.9  O:) 

Seb

---

### Post by kevin1 on 2005-05-03
Thanks for the HowTo Seb.

Downloaded & installed to Hoary OK, but ...

I appear to have a problem with fonts.

The first line in the image was created in OO 1.1 using the Aahs font.

The second line shows how it displays in OO 2.0.

(Thanks to Rhys for the tip re uploading images)

Apart from the fonts being different, the letters run together in OO 2.0, and in general, most text looks messy in OO 2.0.

Thanks for any advice on how to fix this,

Kevin

---

### Post by rhys on 2005-05-03
[QUOTE=dilerra]I used your script and everything worked like a charm.

Just wanted to share my experience of how to customize OO with a custom languagepack (swedish in my case).

1. Download an appropriate languagepack at:
[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m95/](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m95/)

2. Open a terminal and go to the directory where you downloaded the file.

3. Enter the following command:
tail -n +146 OOo_1.9.95_LinuxIntel_langpack_sv.sh > langpack.rpm

4. Next, convert the rpm-file to deb-format:
sudo alien -k langpack.rpm

5. Finally, install the deb-package:
sudo dpkg -i openofficeorg-sv_1.9.95-1_i386.deb

Now you're done! Of course, the files COULD (and probably will =)) have other names on your system. Just start OpenOffice and everything should now be in "your" language =)

Good luck![/QUOTE]


Thank you very much! :)

---

### Post by rhys on 2005-05-03
[QUOTE=kevin1]Thanks for the HowTo Seb.

Downloaded & installed to Hoary OK, but ...

I appear to have a problem with fonts.

The first line in the image was created in OO 1.1 using the Aahs font.

The second line shows how it displays in OO 2.0.

(I hope the image displays ok ~ not too sure how to include images!)

[IMG]/home/kevin/oofonttest.gif[/IMG] 

Apart from the fonts being different, the letters run together in OO 2.0, and in general, most text looks messy in OO 2.0.

Thanks for any advice on how to fix this,

Kevin[/QUOTE]

Try uploading the images using the attachment feature, (click "Go Advanced")

---

### Post by i3dmaster on 2005-05-12
Openoffice comes to 1.9.100, so I just updated the installation script and the Icon package. Also comment out the installation of JRE cause the link the script providing is not available anymore. Thanks Evolution Colt for the initial work!

---

### Post by AndyAWS on 2005-05-12
Cool, thanks.

Do I need to remove the older 1.9 first or does this bring it up-to-date?

---

### Post by sebgate20 on 2005-05-12
[QUOTE=i3dmaster]Openoffice comes to 1.9.100, so I just updated the installation script and the Icon package. Also comment out the installation of JRE cause the link the script providing is not available anymore. Thanks Evolution Colt for the initial work![/QUOTE]
 Sorry but I have been very busy with work at the moment. I hope to have the script update by tomorrow. Thanks i3dmaster for doing that but I'll update the 'offical' version ASAP!

Thanks

Seb

---

### Post by i3dmaster on 2005-05-13
[QUOTE=sebgate20]Sorry but I have been very busy with work at the moment. I hope to have the script update by tomorrow. Thanks i3dmaster for doing that but I'll update the 'offical' version ASAP!

Thanks

Seb[/QUOTE]

Great! That's cool!

---

### Post by stubby on 2005-05-14
[QUOTE=sebgate20]Sorry but I have been very busy with work at the moment. I hope to have the script update by tomorrow. Thanks i3dmaster for doing that but I'll update the 'offical' version ASAP!

Thanks

Seb[/QUOTE]
 great stuff you got there. 
I think there's a minor typo with you webpage though:

wget [http://www.evolutioncolt.com/downloads/EvolutionColt_OO2-0.0.4.tar.gz](http://www.evolutioncolt.com/downloads/EvolutionColt_OO2-0.0.4.tar.gz)

I get a 404 as EvolutionColt_OO2-0.0.4.tar.gz doesn't exist. 0.0.3 does though

---

### Post by robert114 on 2005-05-15
I have used the script from this site and it did the job!  :smile: 

site: [http://www.piai.it/Alberto/doc/ooo-debianize-en.html](http://www.piai.it/Alberto/doc/ooo-debianize-en.html)

I 've used this script after having problems with manualy creating the debian files from the rpm's with alien.

Maybe some one can tell me what went wrong. I just that I like to know what's the problem because i would like to learn from it. I'm using Linux for only a few months and have ubuntu installed since 2 weeks ago

problem:
root@ubuntu:/home/robert/downloads/RPMS # alien -d *.rpm
openofficeorg-calc_1.9.100-2_i386.deb generated
openofficeorg-core01_1.9.100-2_i386.deb generated
openofficeorg-core02_1.9.100-2_i386.deb generated
openofficeorg-core03_1.9.100-2_i386.deb generated
openofficeorg-core03u_1.9.100-2_i386.deb generated
mkdir: cannot create directory `openofficeorg-core04-1.9.100-1.i586.rpm:': File exists
mkdir: cannot create directory `read': File exists
mkdir: cannot create directory `manifest': File exists
mkdir: cannot create directory `failed:': File exists
mkdir: cannot create directory `Success': File exists
sh: line 1: -openofficeorg_core04_1.9.100_1.i586.rpm:: command not found
sh: line 1: -openofficeorg_core04_1.9.100_1.i586.rpm:: command not found
sh: -c: line 2: syntax error near unexpected token `;'
sh: -c: line 2: `; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1'
Unsuccessful stat on filename containing newline at /usr/share/perl5/Alien/Package/Rpm.pm line 166.
mkdir: cannot create directory `openofficeorg-core04-1.9.100-1.i586.rpm: read manifest failed: Success\n-openofficeorg_core04_1.9.100_1.i586.rpm: read manifest failed: Success\n/openofficeorg-core04-1.9.100-1.i586.rpm: read manifest failed: Success\n': No such file or directory
mv: invalid option -- o
Try `mv --help' for more information.
sh: line 1: -openofficeorg_core04_1.9.100_1.i586.rpm:: command not found
sh: line 2: -type: command not found
Argument "openofficeorg-core04-1.9.100-1.i586.rpm:" isn't numeric in bitwise and (&) at /usr/share/perl5/Alien/Package/Rpm.pm line 216, <GETPERMS> line 556.
Unsuccessful stat on filename containing newline at /usr/share/perl5/Alien/Package/Rpm.pm line 235, <GETPERMS> line 556.
mkdir: cannot create directory `openofficeorg-core04-1.9.100-1.i586.rpm:': File exists
mkdir: cannot create directory `read': File exists
mkdir: cannot create directory `manifest': File exists
mkdir: cannot create directory `failed:': File exists
mkdir: cannot create directory `Success': File exists
sh: line 1: -openofficeorg_core04_1.9.100_1.i586.rpm:: command not found
sh: line 2: /debian: No such file or directory
sh: -c: line 2: syntax error near unexpected token `;'
sh: -c: line 2: `; patch -p1)'
sh: line 1: -openofficeorg_core04_1.9.100_1.i586.rpm:: command not found
sh: line 2: -name: command not found
patch failed with .rej files; giving up at /usr/share/perl5/Alien/Package/Deb.pm line 306, <GETPERMS> line 556.
find: openofficeorg-core04-1.9.100-1.i586.rpm: read manifest failed: Success
-openofficeorg_core04_1.9.100_1.i586.rpm: read manifest failed: Success
: No such file or directory
root@ubuntu:/home/robert/downloads/RPMS #

---

### Post by stubby on 2005-05-15
[QUOTE=robert114]I have used the script from this site and it did the job!  :smile: 

Maybe some one can tell me what went wrong. I just that I like to know what's the problem because i would like to learn from it. I'm using Linux for only a few months and have ubuntu installed since 2 weeks ago

[/QUOTE]
try a 
sudo alien -d *.rpm

---

### Post by robert114 on 2005-05-16
well i was allready root. (did sudo su before)

---

### Post by sebgate20 on 2005-05-16
Sorry to all.

Evolution Colt has been extremly busy at the moment. We have moved our server to a new CentOS box. We have update the frontend to Drupal CMS rather than the old Website Baker CMS.

Basically, we are going to be supply products with Ubuntu PRE-INSTALL on them. Machines will be custom built, standard specifications or refirbished machines. Therefore, a lot of planning has been taking place. 

I don't know where else to put this annoucment but hopefully someone might pick it up and move it.

I WILL restore the tutorial (and some new ones we have been working on) as soon as possbile. Hopefully within 24 hours! But things are hectic. So, thanks to the wonderful Ubuntu communtity for all their help and support. You should be seeing a lot more from Evolution Colt soon...  :) 

Seb Payne
Founder and Systems Administrator
Evolution Colt - [www.evolutioncolt.com/mainweb](www.evolutioncolt.com/mainweb)

---

### Post by Marshalus on 2005-05-17
Looking forward to hearing updates to this.

---

### Post by Heliode on 2005-05-18
Offtopic but slightly related: Does anyone know when Openoffice2 will be officially released? And will it be included in future versions of Ubuntu? I already like the betas much more than OOo1.1.*.

---

### Post by robert114 on 2005-05-18
It Can't be to long from now i gues it looks pretty complete to me right now. and I havn't got any stability issues.

But i don't know any date but i'm curious too!!

---

### Post by jdong on 2005-05-18
See [http://www.piai.it/Alberto/doc/ooo-debianize-en.html](http://www.piai.it/Alberto/doc/ooo-debianize-en.html) for a good howto on debianizing Openoffice.org2 beta m100.

It's working beautifully on my system. Only thing is, you can't install it side-by-side with Openoffice.org1.

However, build 100 is stable enough to be usable on a daily basis anyway.

---

### Post by jasplund on 2005-05-18
[QUOTE=jdong]See [http://www.piai.it/Alberto/doc/ooo-debianize-en.html](http://www.piai.it/Alberto/doc/ooo-debianize-en.html) for a good howto on debianizing Openoffice.org2 beta m100.

It's working beautifully on my system. Only thing is, you can't install it side-by-side with Openoffice.org1.

However, build 100 is stable enough to be usable on a daily basis anyway.[/QUOTE]

Will we be seeing it in the backports soon then?


Johan

---

### Post by jdong on 2005-05-18
I'm not planning on it -- perhaps when 2 final comes out, we'll see a backport. Otherwise, it's simply not worth the wasted bandwidth. If 10 people download it, we'll exceed our bandwidth limit!

---

### Post by Heliode on 2005-05-18
[QUOTE=jdong]I'm not planning on it -- perhaps when 2 final comes out, we'll see a backport. Otherwise, it's simply not worth the wasted bandwidth. If 10 people download it, we'll exceed our bandwidth limit![/QUOTE]

What about a torrent of the .deb file? I would certainly be willing to keep it open for as long as I can on my server!

---

### Post by jdong on 2005-05-18
[QUOTE=Heliode]What about a torrent of the .deb file? I would certainly be willing to keep it open for as long as I can on my server![/QUOTE]

excellent idea!
I'll get started on that

---

### Post by jdong on 2005-05-18
Anyone have a BT tracker they're willing to allow me to use? I don't have BT trackers.

Or are you guys OK with making it decentralized? I have an Azureus backport. :)

---

### Post by jasplund on 2005-05-19
I installed it yesterday. It works great. Too bad there's no swedish languagepacks available for linux. Only for ms windows.

---

### Post by benplaut on 2005-05-19
so- should i get 100, like they recomend, or 104, the newest on a few mirrors?

---

### Post by Heliode on 2005-05-19
[QUOTE=jdong]Anyone have a BT tracker they're willing to allow me to use? I don't have BT trackers.

Or are you guys OK with making it decentralized? I have an Azureus backport. :)[/QUOTE]

I can't really help you with a tracker, but you might find [this slashdot article](http://it.slashdot.org/it/05/05/18/2254255.shtml?tid=230&tid=218) interesting.

---

### Post by Laemel on 2005-05-19
[QUOTE=jdong]Anyone have a BT tracker they're willing to allow me to use? I don't have BT trackers.

Or are you guys OK with making it decentralized? I have an Azureus backport. :)[/QUOTE]
 I've got a tracker... pm me, or just upload the file to [ftp://blackmorning.com](ftp://blackmorning.com) (user=guest, no password).

---

### Post by jdong on 2005-05-19
I'm bored. Let's play with decentralized torrenting. I created this with Azureus, and have a 20KB/s upload. Never really tried torrents, much less tried decentralized torrents, in person before.


Let's see the hype. If you'd like to participate, get a client that supports decentralized torrenting. Azureus (in hoary-extras-staging) supports it, and so does the latest Bittorrent beta (i think...).

The torrent is at [http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-3.deb.torrent](http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-3.deb.torrent)

---

### Post by sebgate20 on 2005-05-19
[QUOTE=jdong]I'm bored. Let's play with decentralized torrenting. I created this with Azureus, and have a 20KB/s upload. Never really tried torrents, much less tried decentralized torrents, in person before.


Let's see the hype. If you'd like to participate, get a client that supports decentralized torrenting. Azureus (in hoary-extras-staging) supports it, and so does the latest Bittorrent beta (i think...).

The torrent is at [http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-3.deb.torrent](http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-3.deb.torrent)[/QUOTE]
 Patient Patient. I'm working on hosting the debs soon. Been busy with the new Beagle/Mono stuff at [http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation).

Have a look. The new Wiki rocks! And the guide uses offical packages but it works on Hoary!

Seb

---

### Post by jdong on 2005-05-19
Just an update, we have two people download via decentralized BT, swarming at 20-30KB/s, with me contributing about 18-20KB/s.

I'm pretty impressed with how well this is working. Would be more interesting if more people joined in ;)

The two in there are 87 and 74 percent done respectively, so newcomers will have at least 3 people seeding them. It's shown to give 50KB/s rates ;)

UPDATE: swarm at 70KB/s+, after 3rd client jumped in. Guys who are finishing download, please seed it for a while! Thanks!

---

### Post by Merc248 on 2005-05-19
I'm getting an error when I try to open the .torrent file with gnome-btdownload:

Problem connecting to tracker - <urlopen error unknown type: dht>

Oh yeah, is there a way to remove OpenOffice 1 without clearing out ubuntu-desktop?  Are there even any adverse effects if ubuntu-desktop IS removed?

---

### Post by Laemel on 2005-05-19
[QUOTE=Merc248]I'm getting an error when I try to open the .torrent file with gnome-btdownload:

Problem connecting to tracker - <urlopen error unknown type: dht>

Oh yeah, is there a way to remove OpenOffice 1 without clearing out ubuntu-desktop?  Are there even any adverse effects if ubuntu-desktop IS removed?[/QUOTE]
 That's because he isn't using a real tracker.  He's using an Azureus-only feature instead, so if you want to download the torrent,  you can only use Azureus.

---

### Post by jdong on 2005-05-19
[QUOTE=Laemel]That's because he isn't using a real tracker. He's using an Azureus-only feature instead, so if you want to download the torrent, you can only use Azureus.[/QUOTE]

Well, I though that since I have an apt-gettable Azureus, it's a reasonable request.

---

### Post by Merc248 on 2005-05-19
Yays. Now I'm in the swarm ;p

---

### Post by jdong on 2005-05-19
Whoo, 150KB/s swarm speed :)

---

### Post by NeoChaosX on 2005-05-20
I tried joining in - I installed the newest Azureus and everything - but it isn't working. It connects and the status is "Downloading", but the download rate is 0. What's going on?

---

### Post by Heliode on 2005-05-20
I just tried joining the swarm, but Azureus gave me an error:

Error: no torrent information found in file.

When I tried downloading the torrent again, I got an error as well. Is something wrong?

---

### Post by jdong on 2005-05-20
Hmm, strange. Try this magnet URI with Open Location:

 ```
magnet:?xt=urn:btih:W76BTF5QNUS5RKWGBOCXGJTUIQKNWHTM
```

Take out the spaces between H and TM. The forum is putting that in.

---

### Post by Heliode on 2005-05-20
It says Magnet is an unregistered protocol.

I'm trying to do this on my Gentoo server by the way.

---

### Post by sebgate20 on 2005-05-20
I'm not saying that the torrent isn't a good idea but the idea of providing the script wast that the user could make the latest version themselves. 

Anyway, good luck and hope you get the problems sort it!

Seb

---

### Post by jdong on 2005-05-20
You need Azureus >= 2.3.0.0, or bittorrent >= 4.1.0-beta1

---

### Post by henriquemaia on 2005-05-20
I think is good to have both solutions available. 

I like the script thing, but I'm also seeding now the latest version.

---

### Post by Heliode on 2005-05-20
[QUOTE=jdong]You need Azureus >= 2.3.0.0, or bittorrent >= 4.1.0-beta1[/QUOTE]

Ok, I was still using 2.1.. 2.3 was masked in Gentoo Portage. sorry about that.
To make up for it i'll keep the torrent going for as long as I can! ;)

---

### Post by emendelson on 2005-05-20
Could anyone who has completely downloaded the torrent kindly leave Azureus running afterwards? There have been periods today when no complete copy was available and Azureus was reporting that it would take 249 days to complete the download (which seemed a bit long).  Many thanks!

---

### Post by buildid on 2005-05-20
i have installed or updated  OO with apt-get seems to be fine to me , or is this a bad thing to do ?

---

### Post by jdong on 2005-05-20
Hmm. I've been seeding it nonstop. My internet connection is very crappy recently (always resets), so there may be periods where you lose track of me.

Please do continue seeding the torrent, though. Donate like 5KB/s to us. It doesn't affect you, and you can just stuff it into the system tray.


Also, make sure if you're behind a router, to forward port 6881/**UDP (not just TCP)** to your computer, else distributed tracking won't work! You can also turn on UPNP, and Azureus will take advantage of that.

---

### Post by emendelson on 2005-05-20
UDP 6969? OK, I've enabled that in addition to TCP 6881, which is what Azureus tells me to add. I've still got Azureus open after a complete download, but nobody seems to be taking it - although I was uploading more than downloading a few hours ago. Thanks again for this...

---

### Post by Kyral on 2005-05-20
Firefox won't download the Torrent file :/

I click on it and it displays what looks like XML

---

### Post by jdong on 2005-05-20
Paste the URL into Azureus's Open Location dialog.

---

### Post by emendelson on 2005-05-20
Hmm.. the downloaded deb had something wrong with it, so I deleted and tried again, but this time the .torrent URL didn't work in Azureus or Firefox *and* the Magnet URL (with the extra space removed) didn't work either. Azureus is still searching for it. (The message is Status:Downloading:Searching.) Are the links broken??

EDIT - Wait - turned out I had saved the file elsewhere in a working version. Works perfectly. Thank you!!

---

### Post by jdong on 2005-05-20
Well, the repo was down for most of today. If you go there now, the torrent should open fine with Firefox.

Try downloading again. I had all my seeds abandon me today. If it still doesn't work ,tell me. My network has been acting up recently.


If you've already downloaded successfully, please help me seed.

---

### Post by jdong on 2005-05-20
[QUOTE=emendelson]UDP 6969? OK, I've enabled that in addition to TCP 6881, which is what Azureus tells me to add. I've still got Azureus open after a complete download, but nobody seems to be taking it - although I was uploading more than downloading a few hours ago. Thanks again for this...[/QUOTE]

Sorry, I meant 6881/UDP.

---

### Post by jccalhoun on 2005-05-21
Sweet!  Works well.  Of course OpenOffice.org seems to have come out with a newer beta overnight, but oh well, this will get me through untill the official OpenOffice.org 2.0 comes out.
Thanks!

---

### Post by jdong on 2005-05-21
No problem. I'll make a torrent of the new Openoffice. Though this time I'll use a tracker. Enough fun with decentralized torrenting :)

As much fun as it is, there's still some problems: 
[list=1]
[*]Lack of efficiency. I'm definitely not seeing all the peers and all the seeds, unlike a centralized torrent.   
[*]Network requirements. Extensive use of 6881/udp is required, which not everyone can open. 
[/list]

---

### Post by jdong on 2005-05-21
[http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-104.deb.torrent](http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-104.deb.torrent)

Get your red-hot OOo 1.9.104 debs, now with a tracker ;). You can use whatever client you like!

---

### Post by emendelson on 2005-05-21
OK, I'm connected - but there's no one else there, and no files listed as available...!

---

### Post by jdong on 2005-05-21
shush, I suck at bittorrent ;)

I'm fixing it :)

---

### Post by emendelson on 2005-05-21
Working nicely now - have you tried Azureus for this???

---

### Post by Kyral on 2005-05-21
Sweet thanks! I couldn't use the decentralized one b/c I don't use Azureus (the JRE takes up too much memory for my tastes)

---

### Post by Heliode on 2005-05-22
torrenting! ;) 

I'll keep it up for as long as possible!

When Hoary was released, I managed to get a share rating of around 41 before I had to turn it off, so I'm sure I'll be able to help spread this a bit ;)

---

### Post by jdong on 2005-05-22
Thanks, guys!

I'm at a remote location testing out the torrent, and I can get 65KB/s+ from it. Bittorrent rules!

---

### Post by jdong on 2005-05-22
BTW, for the next two hours, I'll be connected to a fat 180KB/s upload line. Whoever downloads now will be a lucky bastard ;)

---

### Post by buildid on 2005-05-22
get the file and will upload with 85kb/s for a few hours

---

### Post by jdong on 2005-05-22
BTW, I switched trackers... BNBT wasn't working out for me, and bttrack is so much cooler ;). It's PYTHON, come on!

You guys may need to reannounce yourselves.

---

### Post by sebgate20 on 2005-05-22
I have updated the script to work with version m_104. Hopefully OpenOffice.org 2 will make a final release soon!

The instructions are located at: [http://www.evolutioncolt.com/mainweb/?q=node/11](http://www.evolutioncolt.com/mainweb/?q=node/11)

Seb

---

### Post by fargusmax on 2005-05-22
[QUOTE=sebgate20]I have updated the script to work with version m_104. Hopefully OpenOffice.org 2 will make a final release soon!

The instructions are located at: [http://www.evolutioncolt.com/mainweb/?q=node/11](http://www.evolutioncolt.com/mainweb/?q=node/11)

Seb[/QUOTE]
 sebgate20,

I just tried using the directions on the website, and I'm getting a 404 on downloading the non-java script.  Any idea what's wrong?

Rob

---

### Post by jdong on 2005-05-22
Edit your script. Do **NOT** install Java by unpacking the bin into /usr/java, which not only violates FHS and Debian Java policies, but also causes all kinds of incompatibility issues and conflicts.

Install [ftp://ftp2.caliu.info/backports/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update02_i386.deb](ftp://ftp2.caliu.info/backports/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update02_i386.deb)

or sun-j2re1.5 from Backports instead.

---

### Post by fargusmax on 2005-05-22
The instructions need to be updated as well.

3. wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2_nonjava.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2_nonjava.sh) (Non-Java Version)

This step should be:

3. wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh) (Non-Java Version)

Rob

---

### Post by dejitarob on 2005-05-23
Any idea on how to get the kde menus? I've been seeding whenever I get the chance to go online at home, thanks btw.

---

### Post by jdong on 2005-05-23
KDE integration (native widgets, MIME registration ,etc) have NEVER made it into the default OOo builds. Majority of the work in that field was done by Ximian [Novell] and RedHat, so you'll have to compile from source with their patches for KDE native widgets.

---

### Post by dejitarob on 2005-05-24
[QUOTE=jdong]Majority of the work in that field was done by Ximian [Novell] and RedHat, so you'll have to compile from source with their patches for KDE native widgets.[/QUOTE]Is this were the openoffice.org2-kde debian package in the repositories are derived from? I see the few files it installs but it makes some call to a script from the openoffice.org2-debian-files package to install them. ```
# call hook in openoffice.org-debian-files
if [ -x /usr/share/openoffice.org${VER}-debian-files/install-hook ]; then
  /usr/share/openoffice.org${VER}-debian-files/install-hook $THIS_SCRIPT $THIS_PACKAGE "$@"
fi
``` I'm a bit at a loss in my attempt to comprehend this, specifically what this hook does. Is there some kind of verbose argument that would show exactly what this .deb does and where?

---

### Post by jdong on 2005-05-24
These are Ximian packages that the Debian Openoffice team pulled in.


As I've stated before, my .deb was generated from Openoffice.org's binaries, **not from Debian's sources**. That's why it's intentionally named differently (as a SNAPSHOT), that's why it's not in the Backports repository but as a loosely distributed torrent.

---

### Post by dejitarob on 2005-05-26
Yes I understand. I still don't see how the kde deb installs the hooks though. Does anyone know of a easier way to reverse a .deb or some kind of verbose argument that would show exactly what it does and where? Or is it just not possible?

---

### Post by abmcr on 2005-05-26
I  tried to install the latest langpack of OOo 1.9.104 (OOo_1.9.104_LinuxIntel_langpack_it.sh) but the tail command writed as

 tail -n +159 OOo_1.9.104_LinuxIntel_langpack_it.sh > italian.rpm

don't produce a valid rpm file for alien command. In the sh file at line 143 there is:
  $tail_prog +$linenum $0 | gunzip | (cd $outdir; tar xvf -)

Is necessary to launch gunzip? Thank you

---

### Post by lindt on 2005-05-26
try this:  tail -n +159 OOo_1.9.104_LinuxIntel_langpack_it.sh > italian.tar.gz

in the archive there will be three *.rpm, unpack and convert with alien

---

### Post by NateC on 2005-05-29
When will the torrent link will be back up? Or.. will it?

---

### Post by dejitarob on 2005-05-31
[QUOTE=NateC]When will the torrent link will be back up? Or.. will it?[/QUOTE]
[http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh) works fine. I'm still trying to figure out if there is a way to deconstruct a deb so I can possibly port the kde package for the latest beta.

---

### Post by baraider on 2005-06-03
i follow the guide on this thread and get it working....however, along the way, i have to do it couple of times.....

  In the end, i ended up with duplicate icons for everything in the App-office menus...there are 2 icons for everything..

  OpenOffice. org 1.9 Math
  OpenOffice. org 1.9 Math
  .....etc
  The first icon, when clicked, open find, the second, when clicked show this error

Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9.104/program/soffice" (No such file or directory)

  How do i delete the set of invalid second icons or delete anything that left during the botched installation

---

### Post by oddabe19 on 2005-06-03
[QUOTE=baraider]i follow the guide on this thread and get it working....however, along the way, i have to do it couple of times.....

  In the end, i ended up with duplicate icons for everything in the App-office menus...there are 2 icons for everything..

  OpenOffice. org 1.9 Math
  OpenOffice. org 1.9 Math
  .....etc
  The first icon, when clicked, open find, the second, when clicked show this error

Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9.104/program/soffice" (No such file or directory)

  How do i delete the set of invalid second icons or delete anything that left during the botched installation[/QUOTE]
 I get that same one with the writer.
```
Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9.104/program/soffice" (No such file or directory)
```

---

### Post by JuanC on 2005-06-04
In the OpenOffice roadmap says :
[http://development.openoffice.org/releases/OpenOffice_org_2_x.html](http://development.openoffice.org/releases/OpenOffice_org_2_x.html)
> May 2005: OOo 2.0 rc
June 2005 : OOo 2.0
Q3 2005: OOo 2.0.1

There is no OpenOffice 2.0 rc and this is June , Where is OpenOffice 2?

---

### Post by joshchernoff on 2005-06-05
[QUOTE=sebgate20]As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.

This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

Leave any comments here or email me directly at [email]spayne@evolutioncolt.com[/email]. Could a Moderator make this thread a sticky?

Seb Payne
Systems Administrator - Evolution Colt[/QUOTE]
is it all the same for V 1.9.104? i'm having a problem with the editing of the 
javavender.xml file under root shell and I can't seem to login under root 
but when I skip that and go to the next thing to do on that list  witch is some this like 
--shared i get  a decrepped error and it says to use unopkg insted and when I do that I get a error that java runtime can't be found  can some one give  me a pointer  
I'm realy new the linux  thanks

---

### Post by hantms on 2005-06-12
> [http://development.openoffice.org/releases/OpenOffice_org_2_x.html](http://development.openoffice.org/releases/OpenOffice_org_2_x.html)

It seems the link is broken... Any word on a new location for this info?  

Cheers,
Han.

---

### Post by jasplund on 2005-06-12
It works for me

---

### Post by Sionide on 2005-06-12
That link works, make sure you click it rather than copy/pasting... The "r...ce_org" bit isn't the actual URI, it's just to shorten it for the forums.

This link however, doesn't work -> [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)

So, can you post the HOWTO on the actual forum or something? :?

---

### Post by moment on 2005-06-12
Thanks very much. Well done! The link on your first post is broken but I managed to download it from [http://www.evolutioncolt.com/mainweb/?q=node/11](http://www.evolutioncolt.com/mainweb/?q=node/11) 

There are two issues with the script that I mentioned. The first is that jre1.5 which is going to be downloaded by the script is not available anymore (or is not at the moment). The second is that the script doesn't check whether the dpkg database is locked or not. I had Synaptic open in another workspace by mistake.

---

### Post by desdinova on 2005-06-12
I've just installed the latest OO.org - has anyone else noticed the font rendering for some reason isn't quite as good as that in Gnome?

---

### Post by lonetree on 2005-06-18
OpenOffice release 1.9.m109 is out.  Has anyone tried that already? Any idea how to install? Is it the same as the version 1.9.m104?


Regards

---

### Post by jasplund on 2005-06-19
You can download the script "ooo-auto-install-m100-en.sh.gz" from [http://www.piai.it/Alberto/doc/ooo-debianize-en.html](http://www.piai.it/Alberto/doc/ooo-debianize-en.html). Open it in gedit. Change every 1.9.100 to 1.9.109. Also change mandrakelinux to mandriva. Download OOo1.9.109 from [www.openoffice.org](www.openoffice.org) (not necessary). Make the script executable and run the script. This will make you a deb file which you can install with dpkg.

Johan

---

### Post by lonetree on 2005-06-19
I will try this tomorrow, hope it just work the same. Btw, is removing the existing m104 version necessary? If yes, do I just delete the whole directory?

Anyway, I will try this. Will post here.

Just wonder when the actual release will be out.

Regards.

---

### Post by jasplund on 2005-06-19
You can uninstall 104 with synaptic. But only "remove" not "completely remove". Then you can rename /home/*user*/.openoffice.org1.9.104 to .openoffice.org1.9.109 that way you'll keep your settings. After this you should install the deb.

---

### Post by Tomasz on 2005-06-22
I've edited the autoinstall script to use the newest build 1.9.109. 

```

#!/bin/sh

# Download and debianize OpenOffice 2 beta
# 
# ----- Alberto Piai, april 2005
# Released under GNU GPL license
#
# Credits:
# Based on
# http://nathanvi.it/openoffice/index.php?page=DeBianizza by Peo e no0tic

# Requirements:

# -a Java Runtime Environment is needed by OOo for full functionality
# -OOo 1.x COMPLETELY uninstalled from the system
# 
# 

VERSIONE="1.9.109"
HOME=~
WORKDIR=$HOME/.OOotemp3323
CURDIR=`pwd`
FILE_NAME="OOo_1.9.109_LinuxIntel_install.tar.gz"
DOWNLOAD_PATH="ftp://ftp.join.uni-muenster.de/pub/software/OpenOffice/developer/680_m109/OOo_1.9.109_LinuxIntel_install.tar.gz"

test ! -x $WORKDIR || (
	echo "* There's already a $WORKDIR directory..."
	echo "* Rename it or remove it before going on"
	echo "* Or just change the WORKDIR variable in this script!"
	)
test ! -x $WORKDIR || exit 0

if [ -f $CURDIR/$FILE_NAME ];
then
  echo "* Found the tar.gz in this directory!"
  echo "* Not going to download it again"
else
  echo "* Download the tar.gz......"
  wget $DOWNLOAD_PATH
fi  

mkdir $WORKDIR 
cd $WORKDIR
ln -s $CURDIR/$FILE_NAME $WORKDIR/$FILE_NAME

echo "* Extracting tar.gz package....."
tar zxf $FILE_NAME

touch debian-binary
echo "2.0" > debian-binary

echo "* Adapting it to Debian / Ubuntu:"
echo "*    --> removing unnecessary files"

rm -f RPMS/desktop-integration/openofficeorg-redhat-menus-1.9.109-1.noarch.rpm
rm -f RPMS/desktop-integration/openofficeorg-suse-menus-1.9.109-1.noarch.rpm
rm -f RPMS/desktop-integration/openofficeorg-mandriva-menus-1.9.109-1.noarch.rpm

echo "*    --> extracting RPMs........." 
mv RPMS/desktop-integration/openofficeorg-freedesktop-menus-1.9.109-1.noarch.rpm RPMS/
for file in `ls RPMS/*.rpm` ;
	do rpm2cpio $file|cpio -idm &> /dev/null;
done

rm -f RPMS -R

# Crea la directory etc e fai i link necessari
echo "*    --> preparing /etc directory and its links"
mkdir etc
mkdir etc/openoffice.org-1.9
cd etc/openoffice.org-1.9
ln -s ../../opt/openoffice.org1.9.109/share .
ln -s ../../opt/openoffice.org1.9.109/program .
cd ../..

echo "* Packaging data..."
tar zcf data.tar.gz opt usr etc
rm -f opt -R
rm -f usr -R
rm -f etc -R

echo -n "* Packaging .deb file........"

echo "Package: openoffice-snapshot"> control
echo "Version: $VERSIONE" >> control
echo "Architecture: i386" >> control
echo "Description: Snapshot of openoffice m680" >> control

tar zcf control.tar.gz control
rm -f control

ar r openoffice-snapshot_$VERSIONE.deb debian-binary &> /dev/null
rm -f debian-binary
ar r openoffice-snapshot_$VERSIONE.deb control.tar.gz
rm -f control.tar.gz
ar r openoffice-snapshot_$VERSIONE.deb data.tar.gz
rm -f data.tar.gz

echo " OK"

echo "* Cleaning up..."
cp $WORKDIR/*.deb $CURDIR
cd $CURDIR
rm -rf $WORKDIR

echo "* Done!!!"
echo "* If you already uninstalled OpenOffice 1.x"
echo "* install the .deb file with:"
echo "* 	sudo dpkg -i openoffice-snapshot_$VERSIONE.deb"

```

Dla Polaków szybszy b&#281;dzie ten skrypt (For Polish users this script will be faster):

```

#!/bin/sh

# Download and debianize OpenOffice 2 beta
# 
# ----- Alberto Piai, april 2005
# Released under GNU GPL license
#
# Credits:
# Based on
# http://nathanvi.it/openoffice/index.php?page=DeBianizza by Peo e no0tic

# Requirements:

# -a Java Runtime Environment is needed by OOo for full functionality
# -OOo 1.x COMPLETELY uninstalled from the system
# 
# 

VERSIONE="2.0beta-3"
HOME=~
WORKDIR=$HOME/.OOotemp3323
CURDIR=`pwd`
FILE_NAME="OOo_1.9.109_LinuxIntel_install.tar.gz"
DOWNLOAD_PATH="ftp://ftp.man.poznan.pl/pub/openoffice/developer/680_m109/OOo_1.9.109_LinuxIntel_install.tar.gz"

test ! -x $WORKDIR || (
	echo "* There's already a $WORKDIR directory..."
	echo "* Rename it or remove it before going on"
	echo "* Or just change the WORKDIR variable in this script!"
	)
test ! -x $WORKDIR || exit 0

if [ -f $CURDIR/$FILE_NAME ];
then
  echo "* Found the tar.gz in this directory!"
  echo "* Not going to download it again"
else
  echo "* Download the tar.gz......"
  wget $DOWNLOAD_PATH
fi  

mkdir $WORKDIR 
cd $WORKDIR
ln -s $CURDIR/$FILE_NAME $WORKDIR/$FILE_NAME

echo "* Extracting tar.gz package....."
tar zxf $FILE_NAME

touch debian-binary
echo "2.0" > debian-binary

echo "* Adapting it to Debian / Ubuntu:"
echo "*    --> removing unnecessary files"

rm -f RPMS/desktop-integration/openofficeorg-redhat-menus-1.9.109-1.noarch.rpm
rm -f RPMS/desktop-integration/openofficeorg-suse-menus-1.9.109-1.noarch.rpm
rm -f RPMS/desktop-integration/openofficeorg-mandriva-menus-1.9.109-1.noarch.rpm

echo "*    --> extracting RPMs........." 
mv RPMS/desktop-integration/openofficeorg-freedesktop-menus-1.9.109-1.noarch.rpm RPMS/
for file in `ls RPMS/*.rpm` ;
	do rpm2cpio $file|cpio -idm &> /dev/null;
done

rm -f RPMS -R

# Crea la directory etc e fai i link necessari
echo "*    --> preparing /etc directory and its links"
mkdir etc
mkdir etc/openoffice.org-1.9
cd etc/openoffice.org-1.9
ln -s ../../opt/openoffice.org1.9.109/share .
ln -s ../../opt/openoffice.org1.9.109/program .
cd ../..

echo "* Packaging data..."
tar zcf data.tar.gz opt usr etc
rm -f opt -R
rm -f usr -R
rm -f etc -R

echo -n "* Packaging .deb file........"

echo "Package: openoffice-snapshot"> control
echo "Version: $VERSIONE" >> control
echo "Architecture: i386" >> control
echo "Description: Snapshot of openoffice m680" >> control

tar zcf control.tar.gz control
rm -f control

ar r openoffice-snapshot_$VERSIONE.deb debian-binary &> /dev/null
rm -f debian-binary
ar r openoffice-snapshot_$VERSIONE.deb control.tar.gz
rm -f control.tar.gz
ar r openoffice-snapshot_$VERSIONE.deb data.tar.gz
rm -f data.tar.gz

echo " OK"

echo "* Cleaning up..."
cp $WORKDIR/*.deb $CURDIR
cd $CURDIR
rm -rf $WORKDIR

echo "* Done!!!"
echo "* If you already uninstalled OpenOffice 1.x"
echo "* install the .deb file with:"
echo "* 	sudo dpkg -i openoffice-snapshot_$VERSIONE.deb"

```

---

### Post by Dave_is_sexy on 2005-06-23
What's wrong with the openoffice.org2 entries in Synaptic?

---

### Post by Rinnan on 2005-06-24
[QUOTE=Dave_is_sexy]What's wrong with the openoffice.org2 entries in Synaptic?[/QUOTE]
The openoffice.org2 entries in Synpatic are old, for an older version of the beta (m79). The above script gets you version m109. There is a big difference in speed, as well as stability and so on. And besides, in the Linux world -- stuff more than a week old is TOO OLD :)

---

### Post by arnieboy on 2005-06-25
yeah i guess so since I installed openoffice from synaptic today and the stuff keeps crashing at the slightest nudge.. will wait for some quick upgrades in the ubuntu repositories... always helps in upgrading later.. for now, the looks of it are good.. but only if its stable.. i have removed version 1.13.. that was a few decades behind MS Office.

---

### Post by jdong on 2005-06-26
Use the scripts mentioned here to make snapshots. They're far superior to the current Hoary Universe snapshots.

---

### Post by UbuWu on 2005-06-29
[QUOTE=sebgate20]As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.

This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)
[/QUOTE]

404 Not Found

The requested URL /pages/documentation/openoffice-2--ubuntu.php was not found on this server.
Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4 Server at [www.evolutioncolt.com](www.evolutioncolt.com) Port 80

---

### Post by N'Jal on 2005-06-29
tre here [New Page](http://www.evolutioncolt.com/mainweb/?q=node/11)

---

### Post by UbuWu on 2005-06-29
Thanks. Can seb or the moderators edit the first post? So people don't have to go reading all the posts because the link doesn't work...

---

### Post by N'Jal on 2005-06-29
I have tryed this script a couple of times and each time it failed, i will post more on what happened later.

---

### Post by Toz on 2005-06-29
[QUOTE=N'Jal]I have tryed this script a couple of times and each time it failed, i will post more on what happened later.[/QUOTE]
 me too and same problem. I get the following:

***Converting the Packages to the Debian Format***

./
./RPMS/
./RPMS/openofficeorg-gnome-integration-1.9.104-1.i586.rpm
./RPMS/openofficeorg-core01-1.9.104-1.i586.rpm

tar: Read 916 bytes from OOo_1.9.104_LinuxIntel_install.tar.gz
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
rm: cannot remove `openofficeorg-testtool-1.9.104-1.i586.rpm': No such file or directory
rm: cannot remove `desktop-intergration': No such file or directory
openofficeorg-core01_1.9.104-2_i386.deb generated
openofficeorg-gnome-integration_1.9.104-2_i386.deb generated
(Reading database ... 86598 files and directories currently installed.)
Preparing to replace openofficeorg-core01 1.9.104-2 (using openofficeorg-core01_1.9.104-2_i386.deb) ...
Unpacking replacement openofficeorg-core01 ...
Preparing to replace openofficeorg-gnome-integration 1.9.104-2 (using openofficeorg-gnome-integration_1.9.104-2_i386.deb) ...
Unpacking replacement openofficeorg-gnome-integration ...
Setting up openofficeorg-core01 (1.9.104-2) ...
Setting up openofficeorg-gnome-integration (1.9.104-2) ...
chmod: cannot access `/opt/openoffice.org1.9.104/program/soffice': No such file or directory

---

### Post by Toz on 2005-06-29
[QUOTE=Toz]me too and same problem. I get the following:

***Converting the Packages to the Debian Format***

./
./RPMS/
./RPMS/openofficeorg-gnome-integration-1.9.104-1.i586.rpm
./RPMS/openofficeorg-core01-1.9.104-1.i586.rpm

tar: Read 916 bytes from OOo_1.9.104_LinuxIntel_install.tar.gz
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
rm: cannot remove `openofficeorg-testtool-1.9.104-1.i586.rpm': No such file or directory
rm: cannot remove `desktop-intergration': No such file or directory
openofficeorg-core01_1.9.104-2_i386.deb generated
openofficeorg-gnome-integration_1.9.104-2_i386.deb generated
(Reading database ... 86598 files and directories currently installed.)
Preparing to replace openofficeorg-core01 1.9.104-2 (using openofficeorg-core01_1.9.104-2_i386.deb) ...
Unpacking replacement openofficeorg-core01 ...
Preparing to replace openofficeorg-gnome-integration 1.9.104-2 (using openofficeorg-gnome-integration_1.9.104-2_i386.deb) ...
Unpacking replacement openofficeorg-gnome-integration ...
Setting up openofficeorg-core01 (1.9.104-2) ...
Setting up openofficeorg-gnome-integration (1.9.104-2) ...
chmod: cannot access `/opt/openoffice.org1.9.104/program/soffice': No such file or directory[/QUOTE]
 go it. ran the same script 3 times and the third time it worked. must have been a hiccup somewhere...

---

### Post by zerohalo on 2005-06-30
[QUOTE=N'Jal]tre here [New Page](http://www.evolutioncolt.com/mainweb/?q=node/11)[/QUOTE]

I tried that, but when executing the wget command for the non-java version I get a 404 Not Found error.

In navigating the Evolution Colt site itself, the link to the script doesn't seem to work anymore either.

---

### Post by zerohalo on 2005-06-30
[QUOTE=jdong][http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-104.deb.torrent](http://backports.ubuntuforums.org/backports/torrents/openoffice-snapshot_2.0beta-104.deb.torrent)

Get your red-hot OOo 1.9.104 debs, now with a tracker ;). You can use whatever client you like![/QUOTE]

Thanks for doing this, Jdong. I'm prompted for a user/pw when trying to access the above link (whether in Firefox or Azureus). Is there restricted access?

---

### Post by arnieboy on 2005-06-30
same question here. whats the user name and password?

---

### Post by harnadem on 2005-06-30
I found that this command works:
 wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh) (Non-Java Version)

---

### Post by arnieboy on 2005-07-01
when u have 143 posts on a single thread, things get confusing. I think someone like jdong shd start a new thread and give the correct links etc.

---

### Post by arnieboy on 2005-07-01
[QUOTE=harnadem]I found that this command works:
 wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh) (Non-Java Version)[/QUOTE]
yes thanks buddy.. the thing does work. checked it out. maybe u shd start another thread putting this link up so that everyone can use. just make sure to mention that this one is the non-java version.

---

### Post by deBaas on 2005-07-01
[QUOTE=harnadem]I found that this command works:
 wget [http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh](http://www.evolutioncolt.com/downloads/evolutioncolt_oo2.sh) (Non-Java Version)[/QUOTE]
Just open the tekst editor and follow the commands, this way you can easly install the LATEST beta, currently OOo 1.9.113. The script installs 1.9.108

---

### Post by zerohalo on 2005-07-02
I modified the script so that the beta version number (ie 113) can be passed to the script as a parameter. Ie: 
```
$  evolutioncolt_oo2.sh 113
```

This way you can re-use the same script to upgrade to the latest version without having to edit the script each time. OOo2-beta will be installed to /opt/openoffice.org1.9.

I also modified the menu items to point to /opt/openoffice.org1.9 rather than /opt/openoffice.org1.9.xxx so that you don't have to change them each time you upgrade to the latest beta. See attached TAR, which you should download to ~/openoffice2 before running the script below. The script below is modified to work with this tar.

```

# Installation Script for OpenOffice.org 2 Beta (1.9.xxx)
#
# Contact spayne@sebpayne.com with any problems
#
# This script is copyright Evolution Colt 2005.
#
# Modified by zerohalo:
# Accepts OOo2-beta snapshot number as parameter passed to the script.
# Works with modified menu items that point to /opt/openoffice.org1.9.
# Installs OOo2-beta in /opt/openoffice.org1.9
# 
#

echo
echo "Welcome to the Evolution Colt Script for Installing OpenOffice 2 Beta. This has been officaly tested by us on Ubuntu Linux Hoary Hedgehog 5.04. Please Note: If you are promopted with 'Password:', enter your password. This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup. You should cancel it now (Ctrl+C) and run the Java version evolutioncolt_oo2_java.sh as this will install the JRE. You have been warned...."
echo
sleep 10

# Stage 1: Get the Files

echo
echo "***Downloading the Installation File**"
echo
sleep 2

mkdir ~/openoffice2
cd ~/openoffice2
wget http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_install.tar.gz

# Stage 2: Covert the Files to Debian Packages and Installation

echo
echo "***Converting the Packages to the Debian Format***"
echo
sleep 2

tar zxvf OOo_1.9.$1_LinuxIntel_install.tar.gz
cd SRC680_m$1_native_packed-1_en-US.8930/RPMS
rm openofficeorg-testtool-1.9.$1-1.i586.rpm
rm -r desktop-intergration
sudo alien -d *.rpm
rm *.rpm
sudo dpkg -i *.deb
sudo chmod 555 /opt/openoffice.org1.9.$1/program/soffice
sudo mv -f /opt/openoffice.org1.9.$1 /opt/openoffice.org1.9

# Stage 3: Copying the Menu Links

echo
echo "***Menu Links***"
echo
echo "Make sure you've downloaded OOoMenuItems.tar.gz and placed"
echo "it in your ~/openoffice2 folder. If you haven't, open"
echo "another terminal and do so now before continuing."
echo
echo "If OOo2MenuItems.tar.gz is in place, press enter."
echo
read

cd ~/openoffice2
tar zxvf OOo2MenuItems.tar.gz
sudo cp menu/* /usr/share/applications/

# Stage 4: Copying the Icons

echo
echo "***Moving the Icons to the Right Place***"
echo
sleep 1

sudo cp 16x16/* /usr/share/icons/hicolor/16x16/apps/
sudo cp 32x32/* /usr/share/icons/hicolor/32x32/apps/
sudo cp 48x48/* /usr/share/icons/hicolor/48x48/apps/

echo
echo "***Finished! You can now start OpenOffice2.org from the Applications menu***"
echo
sleep 2

```

---

### Post by timczer on 2005-07-02
The updated script by zerohalo worked great.  The only issue I had was that the entries in the applications menu did not point to the correct programs (ended with /programs/soffice -writer etc. while the actual should have been /programs/swriter)  After fixing these it is all good.  I like that I will be able to use the same script to download updates as they come.  Thanks.

---

### Post by zerohalo on 2005-07-02
[QUOTE=timczer]The updated script by zerohalo worked great.  The only issue I had was that the entries in the applications menu did not point to the correct programs (ended with /programs/soffice -writer etc. while the actual should have been /programs/swriter)  After fixing these it is all good.  I like that I will be able to use the same script to download updates as they come.  Thanks.[/QUOTE]

Did .../program/soffice -writer not work for you? Because it works for me. Both .../program/soffice -writer and .../program/swriter (as you put it) yield the same results  on my system (as in, they both launch Writer).

---

### Post by Albaraha on 2005-07-03
Thanks zerohalo.
It works.

---

### Post by timczer on 2005-07-03
One of the icons in the menu did work (I don't remember which one), the other didn't.  The issue was also that it only placed two of the openoffice programs in the office menu.  When I went to smeg it showed all the listings, they just didn't show up in the applications menu.  When I changed the paths in smeg they showed up and worked fine.

---

### Post by disciple3d on 2005-07-03
Thanks for this script!  It works great for me.  I have made a slightly modified version which downloads the OOo2MenuItems.tar.gz.2 file too from my website.  I'm not sure if this is at all useful, but here you go anyway...

[http://www.disciple3d.co.uk/files/evolutioncolt_oo2](http://www.disciple3d.co.uk/files/evolutioncolt_oo2)

---

### Post by manicka on 2005-07-03
Will these menus overwrite the ones previously installed using the evolutioncolt script?

---

### Post by manicka on 2005-07-03
[QUOTE=zerohalo]I modified the script so that the beta version number (ie 113) can be passed to the script as a parameter.
This way you can re-use the same script to upgrade to the latest version without having to edit the script each time. OOo2-beta will be installed to /opt/openoffice.org1.9.

I also modified the menu items to point to /opt/openoffice.org1.9 rather than /opt/openoffice.org1.9.xxx so that you don't have to change them each time you upgrade to the latest beta. See attached TAR, which you should download to ~/openoffice2 before running the script below. The script below is modified to work with this tar.[/quote]

 I keep getting a 404 file not found error when running this script. It appears that the script is not passing the version number corectly. The full error looks like this 

```

--09:02:47--  http://public.planetmirror.com/pub/openoffice/developer/680_m/OOo_1.9._LinuxIntel_install.tar.gz
           => `OOo_1.9._LinuxIntel_install.tar.gz'
Resolving public.planetmirror.com... 203.16.234.91, 203.16.234.19, 203.16.234.20, ...
Connecting to public.planetmirror.com[203.16.234.91]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:02:47 ERROR 404: Not Found.
``` 

I'm using a different mirror but the file is definitely there. The same error occured using the mirror  in the original script as well. My wget entry in the script looks like ```
wget http://public.planetmirror.com/pub/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_install.tar.gz
```  

to make the script I just copied it to a  text file, called it install.sh and ran it with 'sh install.sh' from a terminal.

Any ideas what is wrong?

---

### Post by manicka on 2005-07-03
OK, so I gave up and manually edited the script to 113 and have installed happily.

I don't understand why it didn't work. any thoughts?

---

### Post by qbax on 2005-07-04
Ive experienced serious crash after copying and paste one of the large number of cell s to another sheet in calc  oo 1.9b. Whole system freezed, after rebboting it wont boot up. failed on fsch. Ive fallowed the instructions, run fsch manualy without any parameter, fixed about 35 errors, and some orphan entries (?). then system boot up again and it seems fully functional - but I didn't like that crash. any sugestions ? I'm Ubuntu newbie, Installed oo via synaptic...

---

### Post by manicka on 2005-07-04
The beta version of Ooo that is available through backports (1.9.79)  is very out of date. Remove and try installing using zerohalo's version of the script. This will get you the latest version (113) which has many more bugs ironed out.

---

### Post by vassie on 2005-07-05
zerohalo's script worked a treat, thank you :)
Ben

---

### Post by neongtr on 2005-07-05
i tried but i think the link is broken

---

### Post by manicka on 2005-07-06
You might have the smae problem I did where the script wouldn't pass the latest version number to wget or wget just didn't do the job properly, hence I had to maually edit the script to download the 113 version. Once I did this the script worked perfectly

---

### Post by neongtr on 2005-07-06
oh i see, well I am using 113 but want to have the base feature.

 I just wonder when will 2 become official??

---

### Post by neongtr on 2005-07-06
oh as a newbie, I dont know that opeonoffice is 1.9.113

 silly me...

 how do i edit the script to get the download?

---

### Post by manicka on 2005-07-06
I'n not really sure why the script wouldn't work for me but this edit did. Remember to download the OOoMenuItems.tar.gz file created by zerohalo and place it in ~/openoffice2(/home/*yourusername*/openoffice2)

```
# Installation Script for OpenOffice.org 2 Beta (1.9.xxx)
#
# Contact spayne@sebpayne.com with any problems
#
# This script is copyright Evolution Colt 2005.
#
# Modified by manicka from zerohalo's version:
# Accepts OOo2-beta snapshot number as parameter passed to the script.
# Works with modified menu items that point to /opt/openoffice.org1.9.
# Installs OOo2-beta in /opt/openoffice.org1.9
# 
#

echo
echo "Welcome to the Evolution Colt Script for Installing OpenOffice 2 Beta. This has been officaly tested by us on Ubuntu Linux Hoary Hedgehog 5.04. Please Note: If you are promopted with 'Password:', enter your password. This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup. You should cancel it now (Ctrl+C) and run the Java version evolutioncolt_oo2_java.sh as this will install the JRE. You have been warned...."
echo
sleep 10

# Stage 1: Get the Files

echo
echo "***Downloading the Installation File**"
echo
sleep 2

mkdir ~/openoffice2
cd ~/openoffice2
wget http://public.planetmirror.com/pub/openoffice/developer/680_m113/OOo_1.9.113_LinuxIntel_install.tar.gz

# Stage 2: Covert the Files to Debian Packages and Installation

echo
echo "***Converting the Packages to the Debian Format***"
echo
sleep 2

tar zxvf OOo_1.9.113_LinuxIntel_install.tar.gz
cd SRC680_m113_native_packed-1_en-US.8930/RPMS
rm openofficeorg-testtool-1.9.113-1.i586.rpm
rm -r desktop-intergration
sudo alien -d *.rpm
rm *.rpm
sudo dpkg -i *.deb
sudo chmod 555 /opt/openoffice.org1.9.113/program/soffice
sudo mv -f /opt/openoffice.org1.9.113 /opt/openoffice.org1.9

# Stage 3: Copying the Menu Links

echo
echo "***Menu Links***"
echo
echo "Make sure you've downloaded OOoMenuItems.tar.gz and placed"
echo "it in your ~/openoffice2 folder. If you haven't, open"
echo "another terminal and do so now before continuing."
echo
echo "If OOo2MenuItems.tar.gz is in place, press enter."
echo
read
```

---

### Post by elsewhere on 2005-07-06
[QUOTE=dejitarob]Yes I understand. I still don't see how the kde deb installs the hooks though. Does anyone know of a easier way to reverse a .deb or some kind of verbose argument that would show exactly what it does and where? Or is it just not possible?[/QUOTE]

I pulled my hair out over this for a while, tried different ways including forcing the existing openoffice.org2-kde from the repos and repackaging the deb to make it compatible with the updated ooo2 files etc. etc.  Couldn't get it to work.

However, 113 has now be uploaded to the Breezy repos, including an updated openoffice.org2-kde package.  I installed ooo2 113 from the repos without a problem into Hoary, but the kde package had a lot of dependencies I wasn't comfortable with since they seem to be part of breezy.  I just downloaded the kde package separately, removed the dependencies and installed it straight.  Works perfectly, so now I've got ooo2 with KDE integration.

The drawback is that the performance of the version from the repos seems to lag a bit behind the version I previously installed from this HOWTO, maybe because it's optimized for Breezy, but the kde integration was more important for me so I'll suffer.

Just wanted to throw this in as an option.  Might be possible to install 113 using this howto but download the kde package from breezy and then modify the .deb to install properly into the generic 113 ?

Hope this helps...

Cheers,
KV

---

### Post by zerohalo on 2005-07-06
[QUOTE=manicka]I'n not really sure why the script wouldn't work for me but this edit did. Remember to download the OOoMenuItems.tar.gz file created by zerohalo and place it in ~/openoffice2(/home/*yourusername*/openoffice2)[/QUOTE]

Manicka, I'm curious as to why my version of the script didn't work for you. Were you running the script along with the version number? It seems to me from the error message you reported earlier that perhaps you were just calling the script without including the version number.

The script should be run like this:

$ ./scriptname.sh 113

(scriptname.sh) being whatever you saved the script as. 

if you ran:

$ ./scriptname.sh

then you would get the error message you reported.

The idea behind the script is that when the next OOo version is released, you can run the same script again as:

$ ./scriptname.sh 114

---

### Post by manicka on 2005-07-06
That clears it up for me. 

It would help if I read the instructions properly in the first place :)

Thanks zerohalo :D

---

### Post by jdong on 2005-07-07
[QUOTE=elsewhere]However, 113 has now be uploaded to the Breezy repos, including an updated openoffice.org2-kde package.  I installed ooo2 113 from the repos without a problem into Hoary, but the kde package had a lot of dependencies I wasn't comfortable with since they seem to be part of breezy.  I just downloaded the kde package separately, removed the dependencies and installed it straight.  Works perfectly, so now I've got ooo2 with KDE integration.

The drawback is that the performance of the version from the repos seems to lag a bit behind the version I previously installed from this HOWTO, maybe because it's optimized for Breezy, but the kde integration was more important for me so I'll suffer.
[/QUOTE]
Time out....

Openoffice2 from Breezy is compiled with the GCJ 4.0 native Java system, not to mention that the whole thing is compiled against different versions of GNOME and KDE for integration, different document type support libraries for other file formats (WPD, etc)... Don't try to install OOo2 from Breezy, because it's likely not to be stable. I've already confirmed that the source doesn't compile on Hoary due to it not having all the required libraries!

---

### Post by manicka on 2005-07-07
[QUOTE=jdong]Time out....

Openoffice2 from Breezy is compiled with the GCJ 4.0 native Java system, not to mention that the whole thing is compiled against different versions of GNOME and KDE for integration, different document type support libraries for other file formats (WPD, etc)... Don't try to install OOo2 from Breezy, because it's likely not to be stable. I've already confirmed that the source doesn't compile on Hoary due to it not having all the required libraries![/QUOTE]

Okay, I'm happy to stick with this script until breezy :)

---

### Post by elsewhere on 2005-07-07
[QUOTE=jdong]Time out....

Openoffice2 from Breezy is compiled with the GCJ 4.0 native Java system, not to mention that the whole thing is compiled against different versions of GNOME and KDE for integration, different document type support libraries for other file formats (WPD, etc)... Don't try to install OOo2 from Breezy, because it's likely not to be stable. I've already confirmed that the source doesn't compile on Hoary due to it not having all the required libraries![/QUOTE]

I knew I could be playing with fire drawing from Breezy, but the kde-integration issue was (irrationally) driving me nuts.  My thought with my post was to suggest trying to use the ooo2-kde 113 package from breezy to see if it would work  in the generic 113 downloaded via this hotwo script, I just never tried it myself.  

FWIW, the breezy version is running with more stability on my system than the previous two betas, I've got the kde integration and the interface seems much cleaner.  I'm not recommending it for everyone, but it's suiting my purposes.  In fairness, I don't think I've used any of the modules that require java, since the majority of my work is xls spreadsheets, so I haven't had any java/GCJ issue bite me yet.  As long as I can get by until the official release, I'll be happy...

Cheers,
KV

---

### Post by RaymondQE on 2005-07-08
I didn't have time to wade through all of the pages in this thread, but I was wondering why the script manually sets up the menus when there is a desktop-integration deb package that works pretty well at setting up the openoffice menus.  I believe It even updates the mime information to point to the OOo beta.

---

### Post by zerohalo on 2005-07-08
Since this thread has gotten so long, I'll try to summarize the steps, as they currently stand, so a new reader doesn't have to read through the whole thing:

1. Download the install script found here:
[http://www.disciple3d.co.uk/files/evolutioncolt_oo2](http://www.disciple3d.co.uk/files/evolutioncolt_oo2)

(Script originally written by sebgate20, modified by me, further modified by disciple3d. Hosted by disciple3d.)

2. Save the script anywhere on your computer, call it what you like (ie, oo2-beta-install.sh)

3. Make the script executable:
$ chmod +x oo2-beta-install.sh

4. Run the script as follows:
$ oo2-beta-install.sh xxx

replace xxx with the three digit latest beta version number. currently it's 113. To find the latest version number, look here:

[http://download.openoffice.org/680/index.html](http://download.openoffice.org/680/index.html)

Notes:

- The script will download the latest beta version from the OO site, as well as the menu icons from disciple3d's site. 
- OpenOffice will be installed in /opt/openoffice.org1.9, and menu items will point there.
- The script uses alien to convert the RPMs to DEBs. If you have a problem with alien hanging, run the script again.
- When the next beta release comes out, run the script again, with the new number. Ie, $ oo2-beta-install.sh 114. No need to delete the old installation.
- You can keep your Ubuntu Oo1 or Oo2 installations if you like, though if you're happy with the latest beta, you can uninstall them, via Synaptic, without it affecting the beta install.

Enjoy!

PS. If you find a working DEB of the latest OO2-beta package (it's not in universe/multiverse but you might find it elsewhere), then just use that instead of the script.

---

### Post by arnieboy on 2005-07-08
zerohalo I have a question for you. What happens when i run the script again for lets say beta version 115? will it overwrite beta version 113? or will it install the debs for 115 separately giving us two separate versions of OO (beta 113 and beat 115)? It would be better if this script actually upgrades the installed beta version to the higher beta version. Does it do that?

---

### Post by jasplund on 2005-07-08
Is this the script to use if I have java already or is it not?

the script says: "This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup."

It assumes that I have Sun JRE installed which I do. But it will also destroy my setup of it. I don't get it.

---

### Post by jasplund on 2005-07-08
[QUOTE=zerohalo]Since this thread has gotten so long, I'll try to summarize the steps, as they currently stand, so a new reader doesn't have to read through the whole thing:

1. Download the install script found here:
[http://www.disciple3d.co.uk/files/evolutioncolt_oo2](http://www.disciple3d.co.uk/files/evolutioncolt_oo2)

[/QUOTE]

Is this the script to use if I have java already or is it not?

the script says: "This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup."

It assumes that I have Sun JRE installed which I do. But it will also destroy my setup of it. I don't get it.

---

### Post by manicka on 2005-07-08
[QUOTE=arnieboy]zerohalo I have a question for you. What happens when i run the script again for lets say beta version 115? will it overwrite beta version 113? or will it install the debs for 115 separately giving us two separate versions of OO (beta 113 and beat 115)? It would be better if this script actually upgrades the installed beta version to the higher beta version. Does it do that?[/QUOTE]
 From what I can see the last part of the script should just move the new install to the generic folder and overwrite the old one. Is that correct zerohalo?

---

### Post by manicka on 2005-07-08
[QUOTE=jasplund]Is this the script to use if I have java already or is it not?

the script says: "This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup."

It assumes that I have Sun JRE installed which I do. But it will also destroy my setup of it. I don't get it.[/QUOTE]
 This script is for systems with Java already installed and won't effect your setup if youalready have JRE isnatlled. The message means that it could destroy your setup if you install without JRE installed beforehand.

---

### Post by SpEcIeS on 2005-07-08
That was a great script to install OpenOffice 2.0 Beta (113). Nice improvements, and I believe I am going to remove the 1.1.3 version that comes with Ubuntu, which was nice too. :)

Update:

When trying to remove OpenOffice 1.1.3, synaptic wants to remove Ubuntu.desktop. Is this a good idea or not?  :?  I does not seem to be in my eyes, but who knows?

---

### Post by RaymondQE on 2005-07-09
Removing ubuntu-desktop shouldn't be a problem since it is only a metapackage.  Just make sure you reinstall it before doing a dist-upgrade to breezy.

---

### Post by jasplund on 2005-07-09
I just installed OOo1.9.113 using the script. I didn't install any mimetype icons though.  I had  1.9.109 before which I installed with the italian script. When I uninstalled 109 the mimetype icons where uninstalled as well.


How can I get them back?

---

### Post by jasplund on 2005-07-09
Another thing. since it installs in /opt/openoffice.org1.9 the language packs doesn't work. Cause the languagepack installs in /opt/openoffice.org1.9.113. I copied all the files from 1.9.113 to 1.9 though and now it works


Johan

---

### Post by jasplund on 2005-07-09
Can someone please upload the mimetypeicons?

thanks
Johan

---

### Post by remik on 2005-07-09
I install by:
```
$ oo2-beta-install.sh xxx
``` 

and I can't run:
```
remik@remik:~$ /opt/openoffice.org1.9/program/soffice -writer %U
/opt/openoffice.org1.9/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org1.9/program/soffice.bin: error while loading shared libraries: libcomphelp4gcc3.so: cannot open shared object file: No such file or directory
``` 

What I need to install?

---

### Post by Error1312 on 2005-07-10
Thanks people! The script worked great for me. :)

---

### Post by jpmcc on 2005-07-10
[QUOTE=zerohalo]
1. Download the install script found here:
[http://www.disciple3d.co.uk/files/evolutioncolt_oo2](http://www.disciple3d.co.uk/files/evolutioncolt_oo2)[/QUOTE]
This script still has the 'desktop-inte**[COLOR=Red]r[/COLOR]**gration' typo/bug in it... (as of the date/time of this posting)

John

---

### Post by buellman on 2005-07-10
hi!

a friend found another script for installing latest ooo2 on hoary:
[http://www.glasen-hardt.de/](http://www.glasen-hardt.de/)  <-- german

greets. buellman

---

### Post by clb137 on 2005-07-10
[QUOTE=Seth]That's not a good method at all. Why not just use the debs?

[http://ftp.linux.cz/pub/localizatio....org/devel/680/](http://ftp.linux.cz/pub/localizatio....org/devel/680/)

m97 is even there.[/QUOTE]


That link is not good,  any ideas?


clinton

---

### Post by clb137 on 2005-07-10
Found the link

[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)


thanks

clinton

---

### Post by remik on 2005-07-10
[QUOTE=clb137]Found the link
[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)
[/QUOTE]

Thats OOo2 work?

---

### Post by zerohalo on 2005-07-11
[QUOTE=remik]I install by:
```
$ oo2-beta-install.sh xxx
``` 

and I can't run:
```
remik@remik:~$ /opt/openoffice.org1.9/program/soffice -writer %U
/opt/openoffice.org1.9/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org1.9/program/soffice.bin: error while loading shared libraries: libcomphelp4gcc3.so: cannot open shared object file: No such file or directory
``` 

What I need to install?[/QUOTE]

It looks like you don't have Java installed. You need to install Java first. (You can get it from here: [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp).)

Sorry, I should have made it clearer in my write-up. The script assumes you have Java installed already!

---

### Post by zerohalo on 2005-07-11
[QUOTE=arnieboy]zerohalo I have a question for you. What happens when i run the script again for lets say beta version 115? will it overwrite beta version 113? or will it install the debs for 115 separately giving us two separate versions of OO (beta 113 and beat 115)? It would be better if this script actually upgrades the installed beta version to the higher beta version. Does it do that?[/QUOTE]

I believe it will just overwrite the old beta version, rather than keep it. I originally tried the script using version 109, and then I ran it again with version 113 and it worked.  The DEBs will install to a folder with the version name, but the script takes that folder and renames it to /opt/openoffice.org1.9, thereby overwriting the previous beta version.

Of course this means that if you made any manual changes to those folders, like you added plugins, etc., they'll be overwritten. (I don't mean OO2 settings--those are stored in your ~/.openoffice.org2 folder.)

---

### Post by zerohalo on 2005-07-11
[QUOTE=jasplund]Can someone please upload the mimetypeicons?

thanks
Johan[/QUOTE]

Here you go.

---

### Post by zerohalo on 2005-07-11
[QUOTE=jasplund]Another thing. since it installs in /opt/openoffice.org1.9 the language packs doesn't work. Cause the languagepack installs in /opt/openoffice.org1.9.113. I copied all the files from 1.9.113 to 1.9 though and now it works[/QUOTE]

Also, if you do overwrite your language packs by mistake, you can get them again here:

[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/)

---

### Post by jasplund on 2005-07-11
[QUOTE=zerohalo]Here you go.[/QUOTE]

That's the menu icons. I have those. What I'm looking for is the mimetype icons. The icons for .odt, .ods etc.

Thanks anyway

---

### Post by jasplund on 2005-07-11
[QUOTE=zerohalo]Also, if you do overwrite your language packs by mistake, you can get them again here:

[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/)[/QUOTE]

Yep there's where I got the langpack from in the first place.

---

### Post by jasplund on 2005-07-11
I got the mimetype icons by installing the debian-menu deb. that's in OOo_1.9.113_LinuxIntel_install.tar.gz from the openoffice.org site.

---

### Post by remik on 2005-07-11
[QUOTE=zerohalo]It looks like you don't have Java installed. You need to install Java first. (You can get it from here: [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp).)

Sorry, I should have made it clearer in my write-up. The script assumes you have Java installed already![/QUOTE]

I have j2sdk1.5-sun!

*edit: I don't have symlink to java_vm, now works, thanks:)*

---

### Post by Druke on 2005-07-11
the tutorial link broken?

---

### Post by DancingSun on 2005-07-12
Ah....I wish this is available for Ubuntu AMD64... ](*,)

---

### Post by PaiTrakt on 2005-07-12
Cant say I've read all of the last 20 pages, but I'm getting a 404 on the turorial linked to at page 1. Is there a mirror of it?

EDIT:
Found it:
[http://www.evolutioncolt.com/mainweb/?q=node/11](http://www.evolutioncolt.com/mainweb/?q=node/11)
Note to self: search better the next time.

---

### Post by zerohalo on 2005-07-13
[QUOTE=PaiTrakt]Cant say I've read all of the last 20 pages, but I'm getting a 404 on the turorial linked to at page 1. Is there a mirror of it?

EDIT:
Found it:
[http://www.evolutioncolt.com/mainweb/?q=node/11](http://www.evolutioncolt.com/mainweb/?q=node/11)
Note to self: search better the next time.[/QUOTE]

That script will get you version 104. If you want a newer version, use the script instructions posted a couple of pages back.

---

### Post by abandoned_hussam on 2005-07-14
Can somebody please answer my stupid question? I'm have both OpenOffice1.13(ubuntu) and OpenOffice.org 1.9.117 installed, each in a different directory.
Will 2 installations of Openoffice at once cause problems in the system?

---

### Post by Heliode on 2005-07-14
[QUOTE=hussam]Can somebody please answer my stupid question? I'm have both OpenOffice1.13(ubuntu) and OpenOffice.org 1.9.117 installed, each in a different directory.
Will 2 installations of Openoffice at once cause problems in the system?[/QUOTE]

Nope, I've been running both 1.1.3  and 2.0-beta for quite a while on two machines with no problems.

---

### Post by quick_snack on 2005-07-14
[QUOTE=zerohalo]Also, if you do overwrite your language packs by mistake, you can get them again here:

[http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/](http://oootranslation.services.openoffice.org/pub/OpenOffice.org/680m113/)[/QUOTE]
 And how do I install these packages. They are all scripts wich use rpm to install. How can I install within ubuntu?

---

### Post by Wide on 2005-07-14
Installed oo2 with the script, all was perfect.

Thank you for your efforts :)

---

### Post by manicka on 2005-07-15
[QUOTE=hussam]Can somebody please answer my stupid question? I'm have both OpenOffice1.13(ubuntu) and OpenOffice.org 1.9.117 installed, each in a different directory.
Will 2 installations of Openoffice at once cause problems in the system?[/QUOTE]
 Where did you find 1.9.117. I can't see it on the mirrors yet

---

### Post by manicka on 2005-07-15
[QUOTE=quick_snack]And how do I install these packages. They are all scripts wich use rpm to install. How can I install within ubuntu?[/QUOTE]
 This is what the script in this thread is for. I'd suggest using zerohalo's version a few pages back.

---

### Post by DarkManX4lf on 2005-07-15
the script doesnt work for me here is what i did and what it said.



EDIT - nm i followed zerohalos script + insctructions and it installs fine.


But can i go to synaptic and safely remove the ubuntu openoffice (the one that was installed during ubuntu installation) ?  when i try to do so, it says that ubuntu-desktop is going to be removed as well...should i go ahead and remove it ?

---

### Post by manicka on 2005-07-15
[QUOTE=DarkManX4lf]But can i go to synaptic and safely remove the ubuntu openoffice (the one that was installed during ubuntu installation) ?  when i try to do so, it says that ubuntu-desktop is going to be removed as well...should i go ahead and remove it ?[/QUOTE]
 It's up to you. I've read that you can have both versions installed without any problems. You can also remove ubuntu-desktop and Ooo 1.1.3 if you like. The warning about upgrades etc don't seem to be correct as all my system upgrades etc still happen without it.

---

### Post by arnieboy on 2005-07-15
[QUOTE=manicka]It's up to you. I've read that you can have both versions installed without any problems. You can also remove ubuntu-desktop and Ooo 1.1.3 if you like. The warning about upgrades etc don't seem to be correct as all my system upgrades etc still happen without it.[/QUOTE]
 
The warning about upgrades is about distro upgrade (from hoary to breezy for example).. thats when u need to have ubuntu-desktop installed.

---

### Post by zerohalo on 2005-07-17
[QUOTE=DarkManX4lf]
But can i go to synaptic and safely remove the ubuntu openoffice (the one that was installed during ubuntu installation) ?  when i try to do so, it says that ubuntu-desktop is going to be removed as well...should i go ahead and remove it ?[/QUOTE]

Yes, you can. You'll just have to uninstall ubuntu-desktop (which won't break your system--it's just a placeholder that references Ubuntu's default packages for when you do a dist-upgrade.

---

### Post by wellery on 2005-07-17
I've been told not to remove ubuntu-desktop if you are thinking about upgrading to breezy as having this package makes it a lot easier. I'm not sure if you can install it just before you upgrade though.

---

### Post by manicka on 2005-07-18
[QUOTE=wellery]I'm not sure if you can install it just before you upgrade though.[/QUOTE]
 Yes you can, that's what I'll be doing.

---

### Post by chaumurky on 2005-07-18
[QUOTE=manicka]Yes you can, that's what I'll be doing.[/QUOTE]
 Would you do that *after* you change the repositories to Breezy and 'apt-get update' or before?

---

### Post by manicka on 2005-07-18
[QUOTE=chaumurky]Would you do that *after* you change the repositories to Breezy and 'apt-get update' or before?[/QUOTE]
 before :)

---

### Post by deng on 2005-07-18
Its worked great for me! thx man....

---

### Post by robert114 on 2005-07-19
For those who are interested,

I made Debian install file's from the openofficeorg-base_1.9.113-2_i386 RPMS with Alien.

These debs are working quite well for me! so i 'll share these deb's with bit torrent (I've uploaded the torrent as an attachment)

There is one drawback the menu didn't work. I've installed openofficeorg-debian-menus_1.9.113-1_all.deb too and in KDE i changed the commands  to /etc/openoffice.org-1.9/program/soffice.bin -writer %U for the writer
and /etc/openoffice.org-1.9/program/soffice.bin -calc %U for calc
and so on for the other programs.

This worked fine for me! on KDE

edit: you'll have to remove the .zip extention for the torrent

---

### Post by manicka on 2005-07-19
[QUOTE=robert114]For those who are interested,

I made Debian install file's from the openofficeorg-base_1.9.113-2_i386 RPMS with Alien.

[/QUOTE]

The scripts in this thread will do this for you automatically and fix your menu icon problems as well :)

---

### Post by robert114 on 2005-07-19
[QUOTE=manicka]The scripts in this thread will do this for you automatically and fix your menu icon problems as well :)[/QUOTE]

woops I forgot to mention, but these didn't work for me  :roll:

---

### Post by manicka on 2005-07-19
My advice would be to find zerohalo's version of the script and follow the directions carefully. It should work perfectly for you :D

---

### Post by robert114 on 2005-07-19
[QUOTE=manicka]My advice would be to find zerohalo's version of the script and follow the directions carefully. It should work perfectly for you :D[/QUOTE]

Well, let's hope that the next time i have to install OOF 2 isn't a beta any more!  O:)

---

### Post by zerohalo on 2005-07-19
[QUOTE=chaumurky]Would you do that *after* you change the repositories to Breezy and 'apt-get update' or before?[/QUOTE]

Before. When you install ubuntu-desktop it will automatically remove or restore whatever you changed that caused you to remove ubuntu-desktop in the first place. So it'll put OOo1 back. However, that's not a problem as when you upgrade to Breezy you'll get the latest OO version that comes with Breezy.

---

### Post by Lu-Tze on 2005-07-19
This script was just perfect...worked really well...

thanks a lot...  :smile:

---

### Post by foxy123 on 2005-07-22
m118 is out and they changed the file name, so the script does not work with that version...

---

### Post by jasplund on 2005-07-22
And they updated the dates on the codeline-page  

Plan:

    * OOo 2.0 Beta 2 : August 2005
    * OOo 2.0 Release Candidate : (possibly) September 2005 
    * OOo 2.0 Final : ?? 2005
    * OOo 2.0.1 : 2005/2006

---

### Post by manicka on 2005-07-22
[QUOTE=foxy123]m118 is out and they changed the file name, so the script does not work with that version...[/QUOTE]
 Okay, so just change 
```
OOo_1.9.$1_LinuxIntel_install.tar.gz
```
to
```
OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz
```
in the two parts that it is located in the script and your back in action.

downloading m118 now :D

---

### Post by manicka on 2005-07-22
hmm.stage 2 of the script failed.

Had to do each step manually.

Oh well. 118 up and running :D

---

### Post by foxy123 on 2005-07-22
I wonder if it's easier to download deb packages from ftp.linux.cz and install them manually?

---

### Post by jasplund on 2005-07-22
I don't think there's any gnome-integration-package at ftp.linux.cz. So you won't have the gnome-open/save-thingy

---

### Post by foxy123 on 2005-07-22
[QUOTE=jasplund]So you won't have the gnome-open/save-thingy[/QUOTE]
what is that? I usually used the package from ftp.linux.cz and have not tried the one, which installed with the script (I tried it yesterday, but it was late so I was lazy to make the changes in the script to install m118 ).

---

### Post by jasplund on 2005-07-22
I mean the usual gnome open/save-dialog. I don't recall being able to use that when I installed with the deb's at that cz site. It's no big deal though

---

### Post by foxy123 on 2005-07-22
yeah, Stage 2 does not work since directory structure has been changed slightly as well. I wonder, I have several core files with 'u' besides normal, like core05 and core05u. Should I install both of them or only one and which?

---

### Post by prodi_g on 2005-07-22
I'm still getting the error "Failed to execute child process "/opt/openoffice.org1.9.113/program/soffice" (No such file or directory)".  "dpkg" was not already running so whether or not I was running synaptic at the same time is not a question.  

Someone posted something about modifying menus but I have no clue what that is.  Can someone please help?  Please give detailed instructions.  Thanks.

---

### Post by manicka on 2005-07-22
[QUOTE=foxy123]yeah, Stage 2 does not work since directory structure has been changed slightly as well. I wonder, I have several core files with 'u' besides normal, like core05 and core05u. Should I install both of them or only one and which?[/QUOTE]
 I installed them all and everything is fine

---

### Post by manicka on 2005-07-22
[QUOTE=prodi_g]I'm still getting the error "Failed to execute child process "/opt/openoffice.org1.9.113/program/soffice" (No such file or directory)".  "dpkg" was not already running so whether or not I was running synaptic at the same time is not a question.  

Someone posted something about modifying menus but I have no clue what that is.  Can someone please help?  Please give detailed instructions.  Thanks.[/QUOTE]
 This link will install 113 for you using zerohalo's script. Might be a good place to start if your want the menu's working properly
[http://ubuntuforums.org/showpost.php?p=238119&postcount=147](http://ubuntuforums.org/showpost.php?p=238119&postcount=147)

---

### Post by manicka on 2005-07-22
[QUOTE=foxy123]yeah, Stage 2 does not work since directory structure has been changed slightly as well.[/QUOTE]
 Ah yes, so the line in stage  2 that says
```
cd SRC680_m$1_native_packed-1_en-US.8930/RPMS 
```
should now just be ```
cd RPMS
```

My install script now looks like this ```
 # Installation Script for OpenOffice.org 2 Beta (1.9.xxx)
#
# Contact spayne@sebpayne.com with any problems
#
# This script is copyright Evolution Colt 2005.
#
# Modified by zerohalo:
# Accepts OOo2-beta snapshot number as parameter passed to the script.
# Works with modified menu items that point to /opt/openoffice.org1.9.
# Installs OOo2-beta in /opt/openoffice.org1.9
# 
#

echo
echo "Welcome to the Evolution Colt Script for Installing OpenOffice 2 Beta. This has been officaly tested by us on Ubuntu Linux Hoary Hedgehog 5.04. Please Note: If you are promopted with 'Password:', enter your password. This is the NON-JAVA version which assumes you have the Sun JRE installed. If you do, this could destroy you setup. You should cancel it now (Ctrl+C) and run the Java version evolutioncolt_oo2_java.sh as this will install the JRE. You have been warned...."
echo
sleep 10

# Stage 1: Get the Files

echo
echo "***Downloading the Installation File**"
echo
sleep 2

mkdir ~/openoffice2
cd ~/openoffice2
wget http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz

# Stage 2: Covert the Files to Debian Packages and Installation

echo
echo "***Converting the Packages to the Debian Format***"
echo
sleep 2

tar zxvf OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz
cd RPMS
rm openofficeorg-testtool-1.9.$1-1.i586.rpm
rm -r desktop-integration
sudo alien -d *.rpm
rm *.rpm
sudo dpkg -i *.deb
sudo chmod 555 /opt/openoffice.org1.9.$1/program/soffice
sudo mv -f /opt/openoffice.org1.9.$1 /opt/openoffice.org1.9

# Stage 3: Copying the Menu Links

echo
echo "***Menu Links***"
echo
echo "Make sure you've downloaded OOoMenuItems.tar.gz and placed"
echo "it in your ~/openoffice2 folder. If you haven't, open"
echo "another terminal and do so now before continuing."
echo
echo "If OOo2MenuItems.tar.gz is in place, press enter."
echo
read

cd ~/openoffice2
tar zxvf OOo2MenuItems.tar.gz
sudo cp menu/* /usr/share/applications/

# Stage 4: Copying the Icons

echo
echo "***Moving the Icons to the Right Place***"
echo
sleep 1

sudo cp 16x16/* /usr/share/icons/hicolor/16x16/apps/
sudo cp 32x32/* /usr/share/icons/hicolor/32x32/apps/
sudo cp 48x48/* /usr/share/icons/hicolor/48x48/apps/

echo
echo "***Finished! You can now start OpenOffice2.org from the Applications menu***"
echo
sleep 2

```

Don't forget to have the menu OOo2MenuItems.tar.gz, available at [zerohalo's post](http://ubuntuforums.org/showpost.php?p=238119&postcount=147) , in the directory as well

---

### Post by prodi_g on 2005-07-22
I'm still having trouble.  I've tried multiple people's scripts but to no avail.  For some reason, the "/opt/openoffice.org1.9/program/soffice" is not being created.  Anyone?? 

I tried installing it with synaptic but then I end up with two copies of the OO programs in my menu and I don't know how to remove them.

---

### Post by Sokraates on 2005-07-22
Just because I found out right now: "159" is no longer valid for the "tail"-command. At least for the german langpack  it's "155".

Since it has not yet been mentioned in this thread, here's how to get the correct value:

grep -i -n -a linenum *your_langpack.sh*

The value given for "lineum" is the one you want.

Is there a wildcard or something, where the value given will autmaticaly be used for "tail"? I used a script before to install the langpack, but of course with a fixed value.

Sokraates

---

### Post by manicka on 2005-07-22
The version you have installed with synaptic is 1.1.3. Uninstall 1.1.3 and the duplicate will go away.

To install 118 from the script above. Paste it into a text file called evolutioncolt_oo2.sh and save this into a directory called openoffice2 in your home directory.

Make the script executable. In nautilus, right click on the created file and choose properties. go to the permissions tab and check the boxes to make it executable.

Also make sure that the OOo2MenuItems.tar.gz file (available at link above) is saved in the openoffice2 directory as well.

In a terminal change to the openoffice2 directory and run the command

```
./evolutioncolt_oo2.sh 118
```

The script should now run and install Ooo for you

Enjoy!

---

### Post by prodi_g on 2005-07-22
Thanks manicka.  I got it working now.

---

### Post by zerohalo on 2005-07-23
Thanks, manika, for modifying the script.

For those of you who find the UK mirror slow, you can use a US mirror by changing the 'wget' line in stage one to:

```

wget http://mirrors.isc.org/pub/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz

```

Attached is the icon file the script uses (place it in ~/openoffice2) for those who don't want to have to go digging through old posts to find it :-).

---

### Post by k0304420 on 2005-07-28
I installed openoffice.org2 through Synaptic and now have writer, draw, calc, evolution and impress but what I needed was base and it's not listed. Is there a deb source code I can enter into the repositories to get base?

I really need it, please help!

Jenny.

---

### Post by foxy123 on 2005-07-28
[QUOTE=k0304420]I installed openoffice.org2 through Synaptic and now have writer, draw, calc, evolution and impress but what I needed was base and it's not listed. Is there a deb source code I can enter into the repositories to get base?

I really need it, please help!

Jenny.[/QUOTE]
as it has been said here several times, the version in the repositories is too old (1.9.79 I believe). I would use the script mentioned here if I were you and you'll get Base.

---

### Post by foxy123 on 2005-07-28
[QUOTE=zerohalo]Thanks, manika, for modifying the script.

For those of you who find the UK mirror slow, you can use a US mirror by changing the 'wget' line in stage one to:

```

wget http://mirrors.isc.org/pub/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz

```

Attached is the icon file the script uses (place it in ~/openoffice2) for those who don't want to have to go digging through old posts to find it :-).[/QUOTE]thanks for the update Zerohalo!
I noticed a wierd thing about menues though. They work fine in Gnome, but not so well in xfce that I am using. The thing is that only Printer Admin appeared in xfce menu. All other are missing. Why could it be?

---

### Post by foxy123 on 2005-07-29
ok, I figured it out. So here a little tip for those who use this script with XFCE:

To have OpenOffice in your menu you have to make some changes in your menu files. So if after finishing the script you have only Printer Admin in your menu under Office:

1. Launch a file browser in root mode.

2. Go to /usr/share/applications

3. Find OppenOffice menu files, right-click and go to Properties

4. In Properties select a Launcher tab.

5. Change the Command from for example 
```
/opt/openoffice.org1.9/program/soffice -math %U
``` 
to
```
/opt/openoffice.org1.9/program/smath
``` 

In several seconds you will have the entry in your xfce menu.

6. Do it for all menu files except Printer Admin.

Enjoy!

Could anyone incorporate this tip in the main HOWTO please?

---

### Post by k0304420 on 2005-07-29
Thank you for your advice out of interest is there a step by step guide in how to use the script, I have no idea how to get it to work etc... I'm really new at this and a complete beginner. Any help would be really appreciated.

Thanks,

Jenny xXx

---

### Post by foxy123 on 2005-07-29
[QUOTE=k0304420]Thank you for your advice out of interest is there a step by step guide in how to use the script, I have no idea how to get it to work etc... I'm really new at this and a complete beginner. Any help would be really appreciated.

Thanks,

Jenny xXx[/QUOTE]
the last update should be somewhere in earlier posts. Try to go back a couple of pages or maybe slightly more and you will find the latest script and the comments. 

Basically you have to download the script and run it with ./ specifying the version of the Ooo 2.0 beta. There are some difficulties with 118 version, since you have to make the changes in the script. You will see the comments about it. Just open the script with your favourite text editor and make the changes. (or the script has been already updated?). 

Frankly speaking, this topic became a bit messy.

---

### Post by zerohalo on 2005-07-30
[QUOTE=k0304420]Thank you for your advice out of interest is there a step by step guide in how to use the script, I have no idea how to get it to work etc... I'm really new at this and a complete beginner. Any help would be really appreciated.

Thanks,

Jenny xXx[/QUOTE]

I agree that this forum is messy. We should have this information on a wiki somewhere. Maybe I can try to put it in the Ubuntu wiki. Anyway, for now, here's what to do:

Read this post here for the instructions:
[http://www.ubuntuforums.org/showpost.php?p=246357&postcount=171](http://www.ubuntuforums.org/showpost.php?p=246357&postcount=171)

However, the script has been since modified because OO changed their
naming convention. So get the updated script here:

[http://www.ubuntuforums.org/showpost.php?p=267226&postcount=233](http://www.ubuntuforums.org/showpost.php?p=267226&postcount=233)

You'll need the menu icons, which you can get from here:

[http://ubuntuforums.org/showpost.php?p=238119&postcount=147](http://ubuntuforums.org/showpost.php?p=238119&postcount=147)

That should save you from having to read the 200+ posts in this forum :-)

---

### Post by zerohalo on 2005-07-30
Okay, hopefully this should put this forum to rest!!

Here's a wiki page with the how-to and the script:

[https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta)

If anyone finds any errors there, please correct the wiki page, rather than posting them on this forum. That way future seekers will find the correct information there. Thanks.

---

### Post by Skel on 2005-07-30
whoops ya said dont post errors here ... Link dont work tho :razz:  for the package that is

---

### Post by manicka on 2005-07-30
[QUOTE=Skel]whoops ya said dont post errors here ... Link dont work tho :razz:  for the package that is[/QUOTE]
 What link, for what package?

---

### Post by Skel on 2005-07-30
wget http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz

The link for the wiki page 2 posts up... that link in the guide doesnt work :/

---

### Post by manicka on 2005-07-30
[QUOTE=Skel]wget http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m$1/OOo_1.9.$1_LinuxIntel_rpm_install.tar.gz

The link for the wiki page 2 posts up... that link in the guide doesnt work :/[/QUOTE]
 The file is there. Are you invoking the script with the command

./oo2-beta-install.sh xxx 

xxx shoud be rplaced by the version you want to install. At the moment it's 118, so the comamnd would be 

./oo2-beta-install.sh 118 

The script replaces the m$1 part of this link with the correct version number e.g m118

[QUOTE=zerohalo]Okay, hopefully this should put this forum to rest!!

Here's a wiki page with the how-to and the script:

[https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta)

If anyone finds any errors there, please correct the wiki page, rather than posting them on this forum. That way future seekers will find the correct information there. Thanks.[/QUOTE]

---

### Post by Skel on 2005-07-30
Oh thanks alot :) didnt realize that

---

### Post by jccalhoun on 2005-08-03
So they just released 1.9.122 and the script is failing.  It seems like the reason might be because the script is looking for ...LinuxIntel_rpm_install.tar.gz  and they seem to have named it ....LinuxIntel_install.tar.gz.  
Or is that not an rpm and rpm's will come later?  
I'm a newbie at Linux so I don't know how to tell.

---

### Post by manicka on 2005-08-04
[QUOTE=jccalhoun]So they just released 1.9.122 and the script is failing.  It seems like the reason might be because the script is looking for ...LinuxIntel_rpm_install.tar.gz  and they seem to have named it ....LinuxIntel_install.tar.gz.  
Or is that not an rpm and rpm's will come later?  
I'm a newbie at Linux so I don't know how to tell.[/QUOTE]
 I've updated the wiki, try it now

---

### Post by jccalhoun on 2005-08-04
Thanks.  Now it downloads but I end up getting:

find: openofficeorg-base-1.9.122: No such file or directory
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
chmod: cannot access `/opt/openoffice.org1.9.122/program/soffice': No such file or directory
mv: cannot stat `/opt/openoffice.org1.9.122': No such file or directory

and when I try to start it from the menu I get:

Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9/program/soffice" (No such file or directory)

Any ideas?
Thanks

---

### Post by SpEcIeS on 2005-08-04
Personally, I just got tired of the errors and used alien -d *.rpm and then dpkg -i *.deb with all of the deb's in on directory. After removing the /opt/openoffice.org1.9 directory, containing 113, mv 'ing the /opt/openoffice.org1.9.122 to /opt/openoffice.org1.9.

In a nutshell, just read the script and apply the commands manually. Seems to have worked fine for me. :)

---

### Post by manicka on 2005-08-05
[QUOTE=jccalhoun]Thanks.  Now it downloads but I end up getting:

find: openofficeorg-base-1.9.122: No such file or directory
s[/QUOTE]

What directory is the installer downloaded to?

---

### Post by manicka on 2005-08-05
[QUOTE=SpEcIeS]Personally, I just got tired of the errors and used alien -d *.rpm and then dpkg -i *.deb with all of the deb's in on directory. After removing the /opt/openoffice.org1.9 directory, containing 113, mv 'ing the /opt/openoffice.org1.9.122 to /opt/openoffice.org1.9.

In a nutshell, just read the script and apply the commands manually. Seems to have worked fine for me. :)[/QUOTE]
 Yes, I usually end up doing it that way myself as well, as they seem to be changing the name and directory structure with each release lately

---

### Post by cutOff on 2005-08-05
OOo_1.9.122_LinuxIntel_rpm_install.tar.gz doesn't exist in [that directory](http://www.mirror.ac.uk/mirror/sunsite.dk/openoffice/developer/680_m122/).

---

### Post by JabaSF on 2005-08-09
[QUOTE=remik]I have j2sdk1.5-sun!

*edit: I don't have symlink to java_vm, now works, thanks:)*[/QUOTE]

I have the same problem:

/opt/openoffice.org1.9/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org1.9/program/soffice.bin: error while loading shared libraries: libvcl680li.so: cannot open shared object file: No such file or directory

And I have the sun-j2re1.5 installed (using the backports).

I must be stupid but I don't undestand your solution.

Thks for your help
Bye

---

### Post by SpEcIeS on 2005-08-09
[QUOTE=JabaSF]I have the same problem:

/opt/openoffice.org1.9/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org1.9/program/soffice.bin: error while loading shared libraries: libvcl680li.so: cannot open shared object file: No such file or directory

And I have the sun-j2re1.5 installed (using the backports).

I must be stupid but I don't undestand your solution.

Thks for your help
Bye[/QUOTE]
To create a symbolic link use ln -s [path to link to] [link name].

---

### Post by JabaSF on 2005-08-09
[QUOTE=SpEcIeS]To create a symbolic link use ln -s [path to link to] [link name].[/QUOTE]

SpEcIeS you are very kind to help me but this is not exactly my question. 

Apparently remik had the same problem:

-------------------------------------------------------------------------------------------------------------------------
I install by:
$ oo2-beta-install.sh xxx

and I can't run:
remik@remik:~$ /opt/openoffice.org1.9/program/soffice -writer %U
/opt/openoffice.org1.9/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org1.9/program/soffice.bin: error while loading shared libraries: libcomphelp4gcc3.so: cannot open shared object file: No such file or directory

What I need to install?

It looks like you don't have Java installed. You need to install Java first. (You can get it from here: [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp).)

Sorry, I should have made it clearer in my write-up. The script assumes you have Java installed already!

-------------------------------------------------------------------------------------------------------------------------

zerohalo replyed that he need Java installed (see above), and remik replyed that he had Java installed (so do I). And after he has edited his reply to add that what was missing was a symblink for java_vm. So my question is : a symblink between what and what ?

---

### Post by SpEcIeS on 2005-08-09
Well **JabaSF**, it would seem that you do not really need a symbolic link, but to add your java to the $PATH variable. For example, my java is located in ***/usr/java/jre1.5.0_03***

Now I did not use the backports installation, however I did manually install it.

---

### Post by JabaSF on 2005-08-10
Thanks for your precious help, it's working perfectly with a correct PATH !

And whaou ! This version of oOo  is really great !
Thanks everyone 

Take care
Bye

---

### Post by mre0281 on 2005-08-12
[QUOTE=Tomasz]Modified to newest build 1.9.122. 

```
#!/bin/sh

# Download and debianize OpenOffice 2 beta
# 
# ----- Alberto Piai, april 2005
# ----- Marc Rodriguez, july 2005
# Released under GNU GPL license
#
# Credits:
# Based on
# http://nathanvi.it/openoffice/index.php?page=DeBianizza by Peo e no0tic

# Requirements:

# -a Java Runtime Environment is needed by OOo for full functionality
# -OOo 1.x COMPLETELY uninstalled from the system
# 
# 

VERSIONE="1.9.122"
HOME=~
WORKDIR=$HOME/.OOotemp3323
CURDIR=`pwd`
FILE_NAME="OOo_1.9.122_LinuxIntel_install.tar.gz"
DOWNLOAD_PATH="http://ftp.rediris.es/ftp/mirror/openoffice.org/developer/680_m122/OOo_1.9.122_LinuxIntel_install.tar.gz"

test ! -x $WORKDIR || (
	echo "* There's already a $WORKDIR directory..."
		echo "* Rename it or remove it before going on"
			echo "* Or just change the WORKDIR variable in this script!"
				)
				test ! -x $WORKDIR || exit 0

				if [ -f $CURDIR/$FILE_NAME ];
				then
				  echo "* Found the tar.gz in this directory!"
				    echo "* Not going to download it again"
				    else
				      echo "* Download the tar.gz......"
				        wget $DOWNLOAD_PATH
					fi  

					mkdir $WORKDIR 
					cd $WORKDIR
					ln -s $CURDIR/$FILE_NAME $WORKDIR/$FILE_NAME

					echo "* Extracting tar.gz package....."
					tar zxf $FILE_NAME
					cd SRC*
					mv * ..
					cd ..

					touch debian-binary
					echo "2.0" > debian-binary

					echo "* Adapting it to Debian / Ubuntu:"
					echo "*    --> removing unnecessary files"

					rm -f RPMS/desktop-integration/openofficeorg-redhat-menus-$VERSIONE-1.noarch.rpm
					rm -f RPMS/desktop-integration/openofficeorg-suse-menus-$VERSIONE-1.noarch.rpm
					rm -f RPMS/desktop-integration/openofficeorg-mandriva-menus-$VERSIONE-1.noarch.rpm

					echo "*    --> extracting RPMs........." 
					mv RPMS/desktop-integration/openofficeorg-freedesktop-menus-$VERSIONE-1.noarch.rpm RPMS/
					for file in `ls RPMS/*.rpm` ;
						do rpm2cpio $file|cpio -idm &> /dev/null;
						done

						rm -f RPMS -R

						# Crea la directory etc e fai i link necessari
						echo "*    --> preparing /etc directory and its links"
						mkdir etc
						mkdir etc/openoffice.org-1.9
						cd etc/openoffice.org-1.9
						ln -s ../../opt/openoffice.org$VERSIONE/share .
						ln -s ../../opt/openoffice.org$VERSIONE/program .
						cd ../..

						echo "* Packaging data..."
						tar zcf data.tar.gz opt usr etc
						rm -f opt -R
						rm -f usr -R
						rm -f etc -R

						echo -n "* Packaging .deb file........"

						echo "Package: openoffice-snapshot"> control
						echo "Version: $VERSIONE" >> control
						echo "Architecture: i386" >> control
						echo "Description: Snapshot of openoffice m680" >> control

						tar zcf control.tar.gz control
						rm -f control

						ar r openoffice-snapshot_$VERSIONE.deb debian-binary &> /dev/null
						rm -f debian-binary
						ar r openoffice-snapshot_$VERSIONE.deb control.tar.gz
						rm -f control.tar.gz
						ar r openoffice-snapshot_$VERSIONE.deb data.tar.gz
						rm -f data.tar.gz

						echo " OK"

						echo "* Cleaning up..."
						cp $WORKDIR/*.deb $CURDIR
						cd $CURDIR
						rm -rf $WORKDIR

						echo "* Done!!!"
						echo "* If you already uninstalled OpenOffice 1.x"
						echo "* install the .deb file with:"
						echo "* 	sudo dpkg -i openoffice-snapshot_$VERSIONE.deb"

```

---

### Post by manicka on 2005-08-30
I can't find the thread again, but someone posted a link to the latest 125 relase that is now available as debs.

They installed perfectly for me :) and the best part is that we finally we have some debs that take away the need for installing via scripts.

Install notes: You must remove the latest beta that you have from your system.
For me I did it through synaptic, then went to /opt and deleted the openoffice 1.9 folder. (apt doesn't completely remove it because the script moves it from where apt installed it at the final step.)
You also need to delete the icons that are created by the script (zerohalo's) in /usr/share/applications. 
I did all these jobs with 'sudo nautilus' but I'm sure command line people will know a better way.

Once ready I just untared the deb install file. Changed to the created folder and ran:

sudo dpkg -i *.deb

Much thanks to whoever it was that posted this link
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)

---

### Post by GoA on 2005-08-31
Worked perfectly, thanks. :)

---

### Post by foxy123 on 2005-08-31
[QUOTE=manicka]I can't find the thread again, but someone posted a link to the latest 125 relase that is now available as debs.

They installed perfectly for me :) and the best part is that we finally we have some debs that take away the need for installing via scripts.

Install notes: You must remove the latest beta that you have from your system.
For me I did it through synaptic, then went to /opt and deleted the openoffice 1.9 folder. (apt doesn't completely remove it because the script moves it from where apt installed it at the final step.)
You also need to delete the icons that are created by the script (zerohalo's) in /usr/share/applications. 
I did all these jobs with 'sudo nautilus' but I'm sure command line people will know a better way.

Once ready I just untared the deb install file. Changed to the created folder and ran:

sudo dpkg -i *.deb

Much thanks to whoever it was that posted this link
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)[/QUOTE]

why did yo have to remove enu icons? does this build comes with its own? the previous ones did not have the menu icons/entries as I remember...

---

### Post by GoA on 2005-08-31
It had it's own icons.

---

### Post by foxy123 on 2005-08-31
thanks a lot, worked perfectly for me.... note that 125 is also called Beta 2...

---

### Post by MBro on 2005-08-31
I'm trying to install it from the repo right now but it appears to be down

---

### Post by foxy123 on 2005-09-01
Has anyone tried to install localisation files? I tried GB ones and got an error:

```
 sudo dpkg -i openoffice.org-en-gb_1.9.125-1_i386.deb(Reading database ... 110502 files and directories currently installed.)
Unpacking openoffice.org-en-gb (from openoffice.org-en-gb_1.9.125-1_i386.deb) ...
dpkg: error processing openoffice.org-en-gb_1.9.125-1_i386.deb (--install):
 trying to overwrite `/opt/openoffice.org1.9.125/presets/config/standard.sog', which is also in package openoffice.org-core06
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 openoffice.org-en-gb_1.9.125-1_i386.deb
```

---

### Post by matthew on 2005-09-01
[QUOTE=foxy123]Has anyone tried to install localisation files? I tried GB ones and got an error:[/QUOTE]
I have been having the same problem.

---

### Post by jeffreyvergara.NET on 2005-09-15
[QUOTE=matthew]I have been having the same problem.[/QUOTE]
 hello, I'm new to Linux. I just downloaded "OOo_SRC680_m129_en-US_native_LinuxIntel_install_deb.tar.gz" but i dont know where to go from their. the links on the first post is dead.. i think...

---

### Post by manicka on 2005-09-15
[QUOTE=jeffreyvergara.NET]hello, I'm new to Linux. I just downloaded "OOo_SRC680_m129_en-US_native_LinuxIntel_install_deb.tar.gz" but i dont know where to go from their. the links on the first post is dead.. i think...[/QUOTE]
 Untar the file
Open a terminal
Change to the directory that the tar.gz file created. From memory I think it's called debs

sudo dpkg -i *.deb

---

### Post by RevNomad on 2005-09-15
[QUOTE=sebgate20]Glad I can help  :) 

I've updated the script again so it works properly. I'm thinking of putting OpenOffice.org 2 Beta onto CD-ROM so those without Broadband can take advantage of the new version.

Seb[/QUOTE]

Since I only have dial up I downloaded the deb files for OpenOffice 2 beta last night.  Only............................how do I install from the cd?  My linux laptop has no connection to the net.

NTP

---

### Post by manicka on 2005-09-15
[QUOTE=RevNomad]Since I only have dial up I downloaded the deb files for OpenOffice 2 beta last night.  Only............................how do I install from the cd?  My linux laptop has no connection to the net.

NTP[/QUOTE]
 Copy the downlaoded file from your cd to the linux hardrive and follow the instructions above

---

### Post by RevNomad on 2005-09-16
Oh happy day!  It worked!  Even before I read your response.  

I still haven't learned how to use scripts as opposed DOS batch files.
NTP \\:D/  \\:D/  \\:D/  \\:D/

---

### Post by sk545 on 2005-09-16
umm, so how do i remove this properly after its installed?  I mean, i can't just do 'rm -r /opt/openoffice.org1.9.125'  because that will still show up as being installed with 'dpkg --get-selections'.

---

### Post by manicka on 2005-09-16
[QUOTE=sk545]umm, so how do i remove this properly after its installed?  I mean, i can't just do 'rm -r /opt/openoffice.org1.9.125'  because that will still show up as being installed with 'dpkg --get-selections'.[/QUOTE]
 remove it with apt or synaptic

---

### Post by Technoviking on 2005-09-16
What is the font used in the new OpenOffice2 beta, it is not matching my system font but it is very nice.

---

### Post by sk545 on 2005-09-16
I keep getting this error when i launch it from any of the icons in 'Applications >Office':

```
Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9/program/soffice" (No such file or directory)
```

---

### Post by foxy123 on 2005-09-16
[QUOTE=sk545]I keep getting this error when i launch it from any of the icons in 'Applications >Office':

```
Cannot launch entry

Details: Failed to execute child process "/opt/openoffice.org1.9/program/soffice" (No such file or directory)
```[/QUOTE]
check your path... is you openoffice in that dir? did you install everything?

---

### Post by sk545 on 2005-09-16
well, its kind of confusing since this thread is too long with many script revisions...maybe it used the wrong script?  Here is the one i used:

[https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta)

It installed it in /opt/openoffice.org1.9.125, and i can launch it by using /opt/openoffice.org1.9.125/programs/soffice.bin.  However, the icons do not work.

---

### Post by foxy123 on 2005-09-16
[QUOTE=sk545]well, its kind of confusing since this thread is too long with many script revisions...maybe it used the wrong script?  Here is the one i used:

[https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta)

It installed it in /opt/openoffice.org1.9.125, and i can launch it by using /opt/openoffice.org1.9.125/programs/soffice.bin.  However, the icons do not work.[/QUOTE]
If you had Ooo installed before you may still have menu entries in your home dir... I do not remember where, something like .gnome/apps... anyway find openoffice*.desktop icons in you dir and delete, then new entries will take over.

---

### Post by sk545 on 2005-09-16
Well, i figure that the error is saying this:

Details: Failed to execute child process "/opt/**openoffice.org1.9**/program

But, the script installed it in "/opt/openoffice.org1.9.**125**".  Could this be the problem, and if so, any way to fix it?

/edit: i fixed it.  I had to do these steps manually from the script:


sudo chmod 555 /opt/openoffice.org1.9/program/soffice
sudo mv /opt/openoffice.org1.9 /opt/openoffice.org1.9

I have no idea as to why the script didn't execute the above commands automatically.

---

### Post by SpEcIeS on 2005-09-16
All one has to do is go here: **ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/** download the desired OpenOffice package, and, pending on the distro use the appropriate desktop-integration package.

There is no need to use alien due to the deb package installation tarball.

With regards to the desktop-integration, the deb desktop-integration does not seem to work for Ubuntu, so, with an individual's computer using Ubuntu, I had to manually create shortcuts using SMEG. The SuSE desktop-integration package seems to work fine. :)

The current OpenOffice 2.0 Beta, as of the post, is 129. Works great.  :wink:

---

### Post by sk545 on 2005-09-16
where did you get 129 from?  All i see is 125...

---

### Post by foxy123 on 2005-09-16
[QUOTE=sk545]where did you get 129 from?  All i see is 125...[/QUOTE]
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m129/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m129/)

---

### Post by ghostintheshell on 2005-09-17
Ok! Thank you SpEcIeS!

I downloaded the [OOo_SRC680_m130_en-US_native_LinuxIntel_install_deb.tar.gz]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1/OOo_SRC680_m130_en-US_native_LinuxIntel_install_deb.tar.gz") package from [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1")

Then I :
- Extracted the archive
- cd DEBS
- **sudo dpkg -i *.deb**

And OpenOffice.org 2 (1.9.130) was installed, the menu & shortcuts too!

\\:D/

---

### Post by SpEcIeS on 2005-09-17
[QUOTE=ghostintheshell]Ok! Thank you SpEcIeS!

I downloaded the [OOo_SRC680_m130_en-US_native_LinuxIntel_install_deb.tar.gz]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1/OOo_SRC680_m130_en-US_native_LinuxIntel_install_deb.tar.gz") package from [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m130/Build-1")

Then I :
- Extracted the archive
- cd DEBS
- **sudo dpkg -i *.deb**

And OpenOffice.org 2 (1.9.130) was installed, the menu & shortcuts too!

\\:D/[/QUOTE]
Hey, that's great, and the shortcuts too. :) Things are looking up. One thing though, I did not know OpenOffice 2.0 Beta was now at 130. I best go and have a look and get installing.  :grin:

---

### Post by ghostintheshell on 2005-09-17
[QUOTE=SpEcIeS]Hey, that's great, and the shortcuts too. :) Things are looking up. One thing though, I did not know OpenOffice 2.0 Beta was now at 130. I best go and have a look and get installing.  :grin:[/QUOTE]

The 130 is available since today ;-)

Thank you again, I'm very happy \o/

---

### Post by Hobbsee on 2005-09-29
The release candidate is out - how can we download and install this?  (without compiling it from source, preferably)

The .tar.gz version of openoffice.org 2.0 RC1 is here:
[http://download.openoffice.org/2.0.0rc/index.html](http://download.openoffice.org/2.0.0rc/index.html)

---

### Post by SpEcIeS on 2005-09-30
[QUOTE=Hobbsee]The release candidate is out - how can we download and install this?  (without compiling it from source, preferably)
The .tar.gz version of openoffice.org 2.0 RC1 is here:
[http://download.openoffice.org/2.0.0rc/index.html](http://download.openoffice.org/2.0.0rc/index.html)[/QUOTE]
This may be what you are looking for: [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/OOO680_m1/Build-1](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/OOO680_m1/Build-1) :)

---

### Post by Hobbsee on 2005-09-30
*hides head in shame*

I obviously should have checked there first - I assumed that was only for the betas, and not an RC

Not sure why though...

---

### Post by ghostintheshell on 2005-09-30
there is a little mistake in the RC1 package.
to correct it, just do that after the installation:

```
sudo ln -s /opt/openoffice.org2.0/ /etc/openoffice.org-2.0
``` 

then, the launcher and the menu shortcuts will be ok.

to install the RC1, follow this topic from beginning!
the file to download is now [here]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/OOO680_m1/Build-1/OOo_OOO680_m1_en-US_native_LinuxIntel_install_deb.tar.gz")

enjoy.

---

### Post by one_ro on 2005-09-30
OK I've seen this question asked twice, but no answer...
"How does one uninstall Open Office 1.1?"
I mean, without having to uninstall anything else (i.e. Kubuntu Desktop or anything).
Cheers for any answer!

---

### Post by foxy123 on 2005-09-30
[QUOTE=one_ro]OK I've seen this question asked twice, but no answer...
"How does one uninstall Open Office 1.1?"
I mean, without having to uninstall anything else (i.e. Kubuntu Desktop or anything).
Cheers for any answer![/QUOTE]
What is the problem with uninstalling it? Why removing it through Synaptic does not work for you?

---

### Post by bugi on 2005-09-30
[QUOTE=one_ro]OK I've seen this question asked twice, but no answer...
"How does one uninstall Open Office 1.1?"
I mean, without having to uninstall anything else (i.e. Kubuntu Desktop or anything).
Cheers for any answer![/QUOTE]

Hi, 
Kubuntu Desktop like Ubuntu-Desktop is just "dummy" package and you can safely delete it. Just take a look at summary "It is safe to remove this package if some of the desktop system packages are not desired." you see? :-)

---

### Post by one_ro on 2005-09-30
Pfff, because I have also installed OO2.0beta, and now I have a bunch of openoffice files in Synaptic and I just don't know which ones to select for uninstall.
Of course I looked at the 1.1.3 version, but for example if I try to uninstall openoffic.org-bin version 1.1.3 (first one in the list with this version), synaptic also wants to unistall a few other packages, as well as ubuntu-desktop (see attached png).
As synaptic doesn't tell me the version of the other packages, I just fear not to uninstall the other OObeta.
Well, I thought maybe it's a simple command with apt or something.
Cheers!

---

### Post by one_ro on 2005-09-30
[QUOTE=bugi]Hi, 
Kubuntu Desktop like Ubuntu-Desktop is just "dummy" package and you can safely delete it. Just take a look at summary "It is safe to remove this package if some of the desktop system packages are not desired." you see? :-)[/QUOTE]

Aa-haaaahh!! It worked... thx!

---

### Post by foxy123 on 2005-09-30
[QUOTE=one_ro]Pfff, because I have also installed OO2.0beta, and now I have a bunch of openoffice files in Synaptic and I just don't know which ones to select for uninstall.
Of course I looked at the 1.1.3 version, but for example if I try to uninstall openoffic.org-bin version 1.1.3 (first one in the list with this version), synaptic also wants to unistall a few other packages, as well as ubuntu-desktop (see attached png).
As synaptic doesn't tell me the version of the other packages, I just fear not to uninstall the other OObeta.
Well, I thought maybe it's a simple command with apt or something.
Cheers![/QUOTE]
Select all 1.1.3 packages and uninstall it. Do not care about meta packages.

---

### Post by bugi on 2005-09-30
[QUOTE=ghostintheshell]there is a little mistake in the RC1 package.
to correct it, just do that after the installation:
```
sudo ln -s /opt/openoffice.org2.0/ /etc/openoffice.org-2.0
``` 
then, the launcher and the menu shortcuts will be ok.
to install the RC1, follow this topic from beginning!
the file to download is now [here]("ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/OOO680_m1/Build-1/OOo_OOO680_m1_en-US_native_LinuxIntel_install_deb.tar.gz")
enjoy.[/QUOTE]
Sorry it doesn't work for me. I had to change this line in /usr/bin/openoffice.org-2.0  
to  
```
#!/bin/sh
exec /opt/openoffice.org2.0/program/soffice "$@"
```
Now i can run OpenOffice 2.0 RC1 from command line but still i don't have icons in menu.
Any ideas?

---

### Post by SpEcIeS on 2005-09-30
[QUOTE=bugi]Sorry it doesn't work for me. I had to change this line in /usr/bin/openoffice.org-2.0  
to  
```
#!/bin/sh
exec /opt/openoffice.org2.0/program/soffice "$@"
```
Now i can run OpenOffice 2.0 RC1 from command line but still i don't have icons in menu.
Any ideas?[/QUOTE]
Was the desktop-integration package installed?

---

### Post by bugi on 2005-09-30
[QUOTE=SpEcIeS]Was the desktop-integration package installed?[/QUOTE]

Sure, gnome-integration and debian-menus.

---

### Post by SpEcIeS on 2005-09-30
Hhhhmmm.... I remember having to reconfigure the menu shortcuts for someone manually. Perhaps the shortcut links are incorrect. Try adding these:
[b]
/opt/openoffice.org2.0/program/swriter -> OpenOffice Writer
/opt/openoffice.org2.0/program/sbase -> OpenOffice Base
/opt/openoffice.org2.0/program/scalc -> OpenOffice Calc
/opt/openoffice.org2.0/program/sdraw -> OpenOffice Draw
/opt/openoffice.org2.0/program/simpress - > OpenOffice Impress
/opt/openoffice.org2.0/program/smath -> Math
/opt/openoffice.org2.0/program/soffice -> Basic OpenOffice
[/b]
Add the appropriate icons to suit.
For my SuSE system these are the links that are used:
[b]
openoffice.org-2.0 -base %U
openoffice.org-2.0 -calc %U
openoffice.org-2.0 -draw %U
openoffice.org-2.0 -impress %U
openoffice.org-2.0 -math %U
openoffice.org-2.0-printeradmin
openoffice.org-2.0 -writer %U
[/b]
I hope this helps you out. :)

---

### Post by bugi on 2005-10-01
Hmm and here is another problem, i'm using Gnome 2.10 which doesn't have menu editor tools, how can i edit menu?

---

### Post by ghostintheshell on 2005-10-01
[quote=bugi]Sorry it doesn't work for me. I had to change this line in /usr/bin/openoffice.org-2.0  
to  
```
#!/bin/sh
exec /opt/openoffice.org2.0/program/soffice "$@"
``` Now i can run OpenOffice 2.0 RC1 from command line but still i don't have icons in menu.
Any ideas?[/quote] 
```
 sudo ln -s /opt/openoffice.org2.0 /etc/openoffice.org-2.0 
```
icons will appear in the menu (restart gnome-panel if not).

---

### Post by bugi on 2005-10-01
[QUOTE=ghostintheshell]```
 sudo ln -s /opt/openoffice.org2.0 /etc/openoffice.org-2.0 
```
icons will appear in the menu (restart gnome-panel if not).[/QUOTE]

Nope, still nothing.

---

### Post by manicka on 2005-10-01
[QUOTE=bugi]Hmm and here is another problem, i'm using Gnome 2.10 which doesn't have menu editor tools, how can i edit menu?[/QUOTE]

download the deb for smeg from here

[http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)

sudo dpkg -i smeg.deb

---

### Post by bugi on 2005-10-01
[QUOTE=manicka]download the deb for smeg from here
[http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)
sudo dpkg -i smeg.deb[/QUOTE]

Hi, i had to install newer python-xdg package (i'm using Hoary) and now everything works. Thank you :)
[http://dev.realistanew.com/smeg/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb](http://dev.realistanew.com/smeg/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb)

---

### Post by kawinter on 2005-10-03
[QUOTE=sebgate20]As part of my work at Evolution Colt, I've written a tutorial on installating the latest OpenOffice.org Beta 2 on Ubuntu Linux Hoary Hedgehog.
This tutorial was written for OpenOffice 1.9.95 and has been tested on several machines. You can find the HOWTO at: [http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php](http://www.evolutioncolt.com/pages/documentation/openoffice-2--ubuntu.php)
Leave any comments here or email me directly at [email]spayne@evolutioncolt.com[/email]. Could a Moderator make this thread a sticky?
Seb Payne
Systems Administrator - Evolution Colt[/QUOTE]

I'm getting a 404 error.  Has the HOW TO moved?

---

### Post by manicka on 2005-10-03
[QUOTE=kawinter]I'm getting a 404 error.  Has the HOW TO moved?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=62316&highlight=openoffice+deb](http://www.ubuntuforums.org/showthread.php?t=62316&highlight=openoffice+deb)

---

