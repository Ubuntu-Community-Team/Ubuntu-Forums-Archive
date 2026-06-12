---
title: "Installing &amp; using Twirssi (irssi twitter client)"
date: 2009-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by dannytatom on 2009-01-10
First off, I installed this on [CrunchBang](http://crunchbanglinux.org) but it should work just the same on Ubuntu (as they're both Ubuntu).  Also, this was my first time using CPan, so if there's any questions regarding that I'll try my best to answer but hopefully someone more knowledgeable about that could help.

[Twirssi](http://twirssi.com/) allows you to post to Twitter from as well as:

    * Read your friend feed, and your replies (from people on and not on your feed).
    * Receive and send direct messages (DMs)
    * Use multiple accounts - follow, read and send
    * See the context when your friends reply to users you aren't following

**Before installing** you'll need irssi (duh), Net::Twitter and WWW::Shorten::TinyURL.

[SIZE="5"]Installing Irssi[/SIZE]
Pretty simple:
```

sudo apt-get install irssi

```

I won't go into details on using irssi, but [this guide](http://ubuntuforums.org/showthread.php?p=6365885) should get ya goin' if you've never used it before.



[SIZE="5"]Installing Net::Twitter[/SIZE]

Open up a terminal and run
```

sudo perl -MCPAN -e shell

```
If it's your first time using cpan it'll ask you a few questions about configuring it.  I just typed yes on the first question to let it configure itself, you can do whatever you'd like.

Once it's done loading you should see a cpan[1]>
Type the following: (each one being a seperate command)
```

reload index
install Net::Twitter
 (I recommend typing yes to all the questions of installing other/required modules)

```



[SIZE="5"]Installing WWW::Shorten::TinyURL[/SIZE]
While still in CPan type:
```

install WWW::Shorten::TinyURL

```
This will shorten any url you give it before it tweets, so there's no command you need to use.



[SIZE="5"]Installing Twirssi[/SIZE]
Download the script: [http://twirssi.com/twirssi.pl](http://twirssi.com/twirssi.pl)

Put it in either ~/.irssi/scripts or ~/.irssi/scripts/autorun.  It should be easy to see what the difference is, but if not, scripts in /autorun load when irssi starts.

**& setting it up**
Open a terminal and type the following:
```

irssi
/window new hidden
/window name twitter
/script load ~/.irssi/scripts/autorun/twissir.pl (or wherever you put it)

```

Twirssi should come up in the newly created twitter window.  To have that window come up each time (allowing twirssi to autostart), type **/layout save**  (note that this saves the layout of every window, so be sure to close private messages and unwanted channels first).

To login     -    /twitter_login username password
To tweet    -    /tweet yourstatus
To reply     -    /twitter_reply username:num

To set an account to automatically login type:
/twitter_usernames username
/twitter_passwords password

You can see a full list of the commands [here](http://twirssi.com/index.php?using)

**Edit; forgot a screenshot!**
[[img]http://www.picamatic.com/show/2009/01/11/02/23/1718226_bigthumb.png[/img]](http://www.picamatic.com/view/1718226_2009-01-10-173033_1024x768_scrot/)

Hope this helps somebody. :)

---

### Post by jpeddicord on 2009-01-11
Aaaw, only Twitter? Where's the Identi.ca/laconica love? :p

---

### Post by dannytatom on 2009-01-11
I was wishing the same. ;<

---

### Post by DavidGoodwin on 2009-05-13
If you use a recent enough version, using identi.ca and twitter isn't a problem.

Once the script is loaded etc, you just do, e.g.

/twitter_login thegingerdog blahblah    <- login to twitter
/twitter_login gingerdog@identica blahblah <- login to identi.ca

See also [http://github.com/zigdon/twirssi/commit/e12967f01425466111483936dc139aa2389cdc78](http://github.com/zigdon/twirssi/commit/e12967f01425466111483936dc139aa2389cdc78) which may (or may not) explain it some more.

David.

---

### Post by GrammatonCleric on 2009-06-24
Psst!  Twirssi now supports identi.ca. =)

-GC

---

### Post by BobCFC on 2009-08-15
Thanks this helped a lot.

The last two commands at the end are variables and should read

/set twitter_usernames username
/set twitter_passwords password



(During the first setup be ready to answer yes to more default questions than compiling the kernel!)

---

### Post by abhilashm86 on 2009-08-17
i tried installing Twirssi, it gave these errors, when i try to add Net::Twitter, irssi gives error.....

```
13:32 ***   <(^)                   TWIRSSI v2.2.4 (r659)
13:32 ***    (_(\           http://twirssi.com/ for full docs
13:32 ***     || ` Log in with /twitter_login, send updates with /tweet
13:32 *** Loading WWW::Shorten::TinyURL...
13:32 *** Failed to load Net::Twitter when trying to log in as abhilashm86: Can't locate Net/Twitter.pm in @INC (@INC 
          contains: /home/abhilash/.irssi/scripts /usr/share/irssi/scripts /usr/lib/perl/5.8 /etc/perl 
          /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/share/perl/5.8 
          /usr/local/lib/site_perl .) at (eval 285) line 2.
13:32 BEGIN failed--compilation aborted at (eval 285) line 2.
13:32 
13:32 *** Not logged in!  Use /twitter_login username pass!


```
how to correct this?

---

### Post by abhilashm86 on 2009-08-17
bump!! help

---

### Post by mish on 2009-10-13
As this is one of the top links for twitter and irssi, I thought I would point out that you don't need to use CPAN - the required packages are in the ubuntu repositories - libnet-twitter-perl and libwww-shorten-perl. Install them via your favourite method and then just download twirrsi.pl and you're away. eg using the command line:

```

$ sudo aptitude install libnet-twitter-perl libwww-shorten-perl

```

I had the same problem as abhilashm86 but then I deleted all of ~/.cpan and installed the above and all was sweetness and light :)

---

### Post by andersbk on 2009-12-01
> **mish said:**
> As this is one of the top links for twitter and irssi, I thought I would point out that you don't need to use CPAN - the required packages are in the ubuntu repositories - libnet-twitter-perl and libwww-shorten-perl. Install them via your favourite method and then just download twirrsi.pl and you're away. eg using the command line:

```

$ sudo aptitude install libnet-twitter-perl libwww-shorten-perl

```

I had the same problem as abhilashm86 but then I deleted all of ~/.cpan and installed the above and all was sweetness and light :)

Is this package in Jaunty (9.04)?

I get:
```
Couldn't find any package whose name or description matched "libnet-twitter-perl"
```

TIA.

---

### Post by eagle06 on 2010-01-02
> 19:48 ***   <(^)                   TWIRSSI v2.3.3
19:48 ***    (_(\           [http://twirssi.com/](http://twirssi.com/) for full docs
19:48 ***     || ` Log in with /twitter_login, send updates with /tweet
19:48 *** Loading WWW::Shorten::TinyURL...
19:48 *** Twitter timeout set to 30
19:48 *** Login as 12345@Twitter failed
19:48 *** It's possible you're missing one of the modules required for SSL 
          logins.  Try setting twirssi_avoid_ssl to on.  See 
          [http://cpansearch.perl.org/src/GAAS/libwww-perl-5.831/README.SSL](http://cpansearch.perl.org/src/GAAS/libwww-perl-5.831/README.SSL) for 
          the detailed requirements.



help im getting this error

---

### Post by AlexCuse on 2010-05-29
Great guide - only issue I've run into is that you need to add the Crypt::SSLeay module as well.

Details of how to install it are here: [http://ubuntuforums.org/showthread.php?t=538859](http://ubuntuforums.org/showthread.php?t=538859)

---

