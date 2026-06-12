---
title: "Selecting U-box Software"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by mike acker on 2012-10-18
I'm going to post this in this section as it could be helpful here and there....

In switching from a Win7 system to Ubuntu 12.04 LTS I've been looking at various software to meet my needs

So far, looking pretty good


[LIST=1]
[*]BROWSER: Firefox, no change
[*]e/Mail: Thunderbird: no change
[*]OFFICE: Libre Office (subst. MSFT Office) No Change
[*]FTP: Firefox plug in replaces Ipswitch
[*]gThumb replaces Canon DPP
[*]IRFANVIEW nothing like it!!
[*]Krusader replaces xplorer2
[*]? replaces Clipmate
[*]AUDACITY player replaces Musicbee***
[*]ULTRAEDIT -- Linux version available if really needed; probalby just use Gedit
[*]Audacity no change
[*]Archive manager replaces WinZip
[*]K3B replaces CD Burner
[*]? fileseek
[*]? PGP tool replaces GPA / Kleopatra *
[*]? firewall **
[*]CALENDAR: Continue use of LIGHTNING plug-in for Thunderbird.
[*]DATABASE: MySQL or LIBREOFFICE Base
[/LIST]
~~~
* The ENIGMAIL plug in for THUNDERBIRD includes all the PGP key management  tools needed for working with e/mails; they did a top rate job there. 

** a firewall can be used to isolate a program from internet access; there may be apps for which  this would be preferred.

*** I tried Rhythmbox and Clemtine. then settled on Auidacity player.  the reason: all i want is a player; i do not want internet service with it.   Audacity allows me to slap together a morning playlist from my existing music library.

---

### Post by ajgreeny on 2012-10-18
> BROWSER: Firefox, no change
e/Mail: Thunderbird: no change
OFFICE: Libre Office (subst. MSFT Office) No Change
FTP: Firefox plug in replaces Ipswitch
gThumb replaces Canon DPP
IRFANVIEW nothing like it!!
Krusader replaces xplorer2
? replaces Clipmate
? replaces Musicbee
ULTRAEDIT -- Linux version available if really needed; probalby just use Gedit
Audacity no change
Archive manager replaces WinZip
? replaces CD Burner
? fileseek
Try parcellite in place of clipmate, and are you aware that Irfanview works great through wine, the irfanview dev even says so on his site.
k3b is probably the best CD Burner available ion Linux.

---

### Post by mike acker on 2012-10-18
> **ajgreeny said:**
> Try parcellite in place of clipmate, and are you aware that Irfanview works great through wine, the irfanview dev even says so on his site.
k3b is probably the best CD Burner available ion Linux.

thanks for the tips; i'll be checking them out!!

-- anybody try Turbotax via Wine ?

---

### Post by oldos2er on 2012-10-18
See [http://appdb.winehq.org/objectManager.php?sClass=application&iId=623](http://appdb.winehq.org/objectManager.php?sClass=application&iId=623)

---

### Post by mike acker on 2012-10-18
> **oldos2er said:**
> See [http://appdb.winehq.org/objectManager.php?sClass=application&iId=623](http://appdb.winehq.org/objectManager.php?sClass=application&iId=623)

vfi, I'll take this under advisement. it may be best to use the web version

---

### Post by mike acker on 2012-10-19
i tried out the CD Burners we have available,--
xfburn
brasereo
K3B

of these i like K3B although i must note thatit is missing the scramble tracks feature as well as the ability to print a label -- which i really liked in CDburnerXP

---

### Post by StinkySQL on 2012-10-19
You might want to look at BlueFish for the replacement editor.

[http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)

---

### Post by juancarlospaco on 2012-10-19
> **mike acker said:**
> [LIST=1]
[*]gThumb replaces Canon DPP
[*]IRFANVIEW nothing like it!!
[/LIST]

[http://getsilicon.org/limoo](http://getsilicon.org/limoo)

> **mike acker said:**
> [LIST=1]
[*]? replaces Musicbee
[/LIST]

[http://www.clementine-player.org](http://www.clementine-player.org)

> **mike acker said:**
> [LIST=1]
[*]K3B replaces CD Burner
[/LIST]

[http://getsilicon.org](http://getsilicon.org)

> **mike acker said:**
> [LIST=1]
[*]? fileseek
[/LIST]

[http://twotoasts.de/index.php/catfish](http://twotoasts.de/index.php/catfish)

---

### Post by mike acker on 2012-10-19
> **juancarlospaco said:**
> 
photography: [http://getsilicon.org/limoo](http://getsilicon.org/limoo)
music: [http://www.clementine-player.org](http://www.clementine-player.org)
CD/DVD:[http://getsilicon.org](http://getsilicon.org)
Search:[http://twotoasts.de/index.php/catfish](http://twotoasts.de/index.php/catfish)

thanks for the recommendations!!  I'll look into the Clementine player next.  i did a little research on it using Google to check for reviews: the program appears to be well recommended

[ SOFTPEDIA review]("http://www.softpedia.com/reviews/linux/Clementine-Review-255776.shtml")

I thought, as long as I'm going through the windows to Linux software substitutions thing -- i might just keep my notes online here -- could be useful to another person looking at the same or similar questions

i think if i select a software package from the Ubuntu supplied software library I should reasonably expect the program is known to the group and has been found to be free of badware

in looking at a net download though i think it is important to do a little checking... after all: I'm going to provide the administrator password and let this stuff install into my system... I better know i'm installing an OK package.

***software distro's should be signed with PGP. this is necessary to protect downloaders from counterfeits.*** to do this I need a PGP key from Canonical -- that I can check.  after I check it -- I can sign it and authorize it to sign for other keys.   then, on a package like this Clementine I would expect the developer's signature to have been signed with Canonical's software key -- and that signature would check against my system. *

I noticed GnuPG comes pre-installed on Ubuntu.  that is *excellent*.

but the easiest and favorite way hackers get malware into their victims -- is to just get the system owner to install it:(

in terms of the signed distro: what PGP does with theirs: (1) zip up the distro (2) sign the zip thus generated (3) zip the distro plus the signature creating the download pack.  I used to load PGP professional onto the hospital server -- and that's how they sent it out.
~~~
* do we have a PGP section here ?   [GnuPG has their own user group and discussion letter ]("http://lists.gnupg.org/mailman/listinfo/gnupg-users") but a beginner section here might not hurt

---

### Post by juancarlospaco on 2012-10-19
From Repos, it uses Signs and Hashes sir, its documented, going OT anyways.

---

### Post by mike acker on 2012-10-20
> **juancarlospaco said:**
> From Repos, it uses Signs and Hashes sir, its documented, going OT anyways.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

i noticed that.

but in this as in so many attempts at authentication they
miss the Critical Element: I have NOTHING to check their
signature against. a counterfeit can be supplied, with a
counterfeit signature.

this is a fundamental failure to apprehend how Public Key
Encryption Trust Models operate. 

I will sign this message for you. and you will recognize the
same problem: you have NOTHING to check my signature with:
it is MEANINGLESS without that check.

Microsoft, for example, now signs all Security Bulletins
with a PGP signature.  I went out to their site and got a
copy of their key.  Having done that, I can sign their key,
indicating that I trust that I have done due diligence, that
I am satisfied that I have a correct copy of their key.

having done these things, Thunderbird now shows their
messages as authenticated.

Public Key Encryption is more than encryption: it is
integrity and authentication as well.  Our failure to
apprehend these requirements facilitates hacking in a major
way.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v2.0.17 (MingW32)

iQEcBAEBAgAGBQJQgpwTAAoJEGzxM/HQiIDDjk8H/3Vh029ujoqHXJIwsZPjDuut
uf2NrrKqO5uTOKGSHCGWAWf3WQMqSMRUnkeNHpy9L572AR6u0pCDK1xgCaSEXrbM
hZDvgtJvWbLNpzpxWm1dIBDh75UUJvJATPdDhIpnd6aH+F+4VCjhUBkBOSj5D1TZ
pjcGkk109+mAj4Hq9ynEqGU0ollLtsufPl3Sh6VjFoCOuWpV1QcTIm5Qdn40CnSS
sIo66CLT/0Mvokq2U0V21C89k0kCwjxHCiOt1HDiFHKQWhgDuYmJRM/5zzPfHf9p
kx5uSL+xwIZaHrTuTZFwHwwn4d9aE+7VyO9dK+x19JYaftCGtpxFcRYJh0QMe2U=
=OInP
-----END PGP SIGNATURE-----

---

### Post by juancarlospaco on 2012-10-20
Ubuntu comes with CLI (gpg*) and GUI (seahorse) sir, its documented, going OT anyways.

---

### Post by mike acker on 2012-10-29
So far, looking pretty good


[LIST]
[*]    BROWSER: Firefox, no change
[*]    e/Mail: Thunderbird: no change
[*]    OFFICE: Libre Office (subst. MSFT Office) No Change
[*]    FTP: Firefox plug in replaces Ipswitch
[*]    gThumb replaces Canon DPP
[*]    IRFANVIEW nothing like it!!
[*]    Krusader replaces xplorer2
[*] ? replaces Clipmate
[*]AUDACITY player replaces Musicbee***
[*]    ULTRAEDIT -- Linux version available if really needed; probalby just use Gedit
[*]    Audacity no change
[*]    Archive manager replaces WinZip
[*]    K3B replaces CD Burner
[*]    ? fileseek
[*]    ? PGP tool replaces GPA / Kleopatra *
[*]    ? firewall **
[*]    CALENDAR: Continue use of LIGHTNING plug-in for Thunderbird.
[*]    DATABASE: MySQL or LIBREOFFICE Base
[/LIST]
Clipit -- replaces Clipmate
AppArmor -- replaces A/V and Firewall
GPA -- command line
Audacious -- replaces MusicBee
SearchMonkey -- testing -- replace fileseek

Putting Thunderbird and Firefox under containment(AppArmor) will probably provide better protection than any post-hoc a/v package

---

### Post by zombifier25 on 2012-10-29
For a ClipMate replacement, [Glippy](https://launchpad.net/glippy) looks promising.

---

### Post by mike acker on 2012-10-29
> **zombifier25 said:**
> For a ClipMate replacement, [Glippy]("https://launchpad.net/glippy") looks promising.

thanks.

the main thing that Clipmate had -- which is missing now -- is the archive folders.  I used to keep a few references there that I needed to use occasionally,-- in these recurring discussions,-- here & elsewhere...

right now I'm working to get a working knowledge of AppArmor .

it is my feeling we should have absolute control over the programs that run in our systems, particularly regarding: what can be accessed, and what may be exfiltrated

it is important to note that while all of us here are Good Guys nonetheless there are bad guys "out there" -- who find ways to mis-use data in ways we likely won't think of

Electronic Privacy, IMHO, is covered under Amendment IV.  Still, it's incumbent upon each of us to exercise due diligence in the protection of our "papers".

---

