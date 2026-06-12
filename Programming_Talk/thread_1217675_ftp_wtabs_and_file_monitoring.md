---
title: "ftp w/tabs and file monitoring"
date: 2009-07-19
forum: Programming Talk
---

### Post by phazei on 2009-07-19
I'm a PHP developer and often I'm working on multiple sites at once.  I want to move to Ubuntu exclusively.  In windows I use SmartFTP.  I'm looking for a FTP client that will monitor as many files as I choose to edit and automatically upload them to the ftp servers on save.  I'd prefer it to use tabs for multiple sites as it's easier than having an extra 3-4 items on the task panel.

---

### Post by dlmarti on 2009-07-19
There are sooo many ftp clients for Linux its not even funny.
Personally I use ncftp, its a really old command line program, but I love it.

filezilla is always a good one, and you can always setup bookmarks under your "places" for this type of thing.

rdist, scp, svn, all play a role in my software roll outs.  ncftpput, ncftpget, are all good options.

---

### Post by phazei on 2009-07-19
I can understand a cli ftp program if you just need to upload a single batch of files, but I don't understand how it could be used productively when there are lots of files.

I sometimes need to be editing like 20+ files at a time, so I would have to continually browse to 20 different locations and individually download and upload the files over and over again, that would take so much time.  With a GUI, you just click and edit.

I've looked at many of the GUI ftp programs, but none of them have the functionality many of the windows programs have.  I was hoping there was something I missed that would allow me to maintain my productivity in linux.

I need a program where I can click edit on as many files as I want, and each time I save, it will automatically upload the new version to the ftp.  It's rather common functionality in windows.  It seems all that linux has to offer is plain basic functionality, where actually being able to save multiple locations is an 'oohh aahh' feature.  Linux is where GUI ftp was in the 90's for windows.

---

### Post by monraaf on 2009-07-19
> **phazei said:**
> It seems all that linux has to offer is plain basic functionality, where actually being able to save multiple locations is an 'oohh aahh' feature.  Linux is where GUI ftp was in the 90's for windows.

You obviously don't know what you are talking about. I suggest you do some proper investigation before you start trashing Linux.

---

### Post by phazei on 2009-07-20
> **monraaf said:**
> You obviously don't know what you are talking about. I suggest you do some proper investigation before you start trashing Linux.

My apologies, I wasn't trying to trash Linux, just stating my opinion based on what I've found.

You're statement that "* obviously don't know what [I'm] talking about" is as baseless as your perception of my statement.  I've done research to back up what I said.  I would be most humbled and grateful to you if you were to prove me wrong with something to backup what [I]you* said.

I've looked, and the best I've found is FileZilla, and it is crap.  The GUI doesn't have any modern day features.  No modularity, no tabs, can't adjust placements of anything, fixed panes (can only change size, not location or closing).  FireFTP was so-so, but very slow and I can't restart firefox without closing it, it's not it's own program.

I ask for GUI suggestions and get CLI responses.  Ubuntu is all about making linux easy and bringing it to the public, if that's the case, CLI is yesternews.

I'm not asking for anything extravagant, just something that will let me do my job fast in linux, with the same functionality that appears to be common in windows.

---

### Post by Cyanidepoison on 2009-07-20
You don't need a special FTP client to do this.  Just write a script to monitor if the file has changed, and if it has changed upload it to the server.  Just run this script in the background as you're working on a set of files, it'll work the same way.

---

### Post by ad_267 on 2009-07-20
I've never come across the automatic upload after saving feature but then I've only used gFTP which suits my needs fine as well as a few others in Windows.

The Wikipedia comparison might be a good place to start looking: [http://en.wikipedia.org/wiki/Comparison_of_FTP_client_software](http://en.wikipedia.org/wiki/Comparison_of_FTP_client_software)

CrossFTP looks pretty good but you have to pay for the pro version.

One thing you might want to look into is just using the file browser (Nautilus) to access your sites.

---

### Post by phazei on 2009-07-20
> **Cyanidepoison said:**
> You don't need a special FTP client to do this.  Just write a script to monitor if the file has changed, and if it has changed upload it to the server.  Just run this script in the background as you're working on a set of files, it'll work the same way.

So if I have a site with 500 files in different locations, does the script have to be told where every single one needs to be uploaded?  And be updated every time a new file is created?  And duplicated across 20 sites?  If I want to quickly change a typo on a site, I need to write a script to upload that file after I saved it?

The point to automatic upload after saving is to save time. So I open, edit, save, done.  Nothing else, so it's fast and more efficient.  It's common in many windows ftp clients.


> **ad_267 said:**
> I've never come across the automatic upload after saving feature but then I've only used gFTP which suits my needs fine as well as a few others in Windows.
....
One thing you might want to look into is just using the file browser (Nautilus) to access your sites.

It's a very usefull feature.  SmartFTP and CuteFTP are just two of many clients that support it. I never knew how much easier things could be till I used it, wow.


I tried to use Nautilus, then I could just edit the files out wright and it would be great.
If I type [ftp://ftp.site.com](ftp://ftp.site.com) it asks for the password, then says:
'Nautilus cannot handle "ftp" locations.'

If I click Places > Connect to Server, it says:
'Cannot display location "ftp://user@ftp.site.com/"
Operation unsupported'

Ubuntu 9.04

---

### Post by Cyanidepoison on 2009-07-20
> **phazei said:**
> So if I have a site with 500 files in different locations, does the script have to be told where every single one needs to be uploaded?  And be updated every time a new file is created?  And duplicated across 20 sites?  If I want to quickly change a typo on a site, I need to write a script to upload that file after I saved it?

The point to automatic upload after saving is to save time. So I open, edit, save, done.  Nothing else, so it's fast and more efficient.  It's common in many windows ftp clients.


Shell wildcards are a blessing, use them.

And my solution does everything you say that you need.



Look, you're obviously not used to the way Linux does things.  People don't write software like CuteFTP for Linux, they don't need it.  A simple shell script saves a lot of time and doesn't require paying a license fee.

---

### Post by phazei on 2009-07-20
> **phazei said:**
> Linux is where GUI ftp was in the 90's for windows.

gFTP now:
[IMG]http://gftp.seul.org/gftp-screenshot.png[/IMG]
WS_FTP95:
[IMG]http://www.ust.hk/itsc/multimedia/g2server/gif/newftp.gif[/IMG]
WS_FTP now:
[IMG]http://wizzersays.com/wp-content/uploads/2009/03/ws_ftp2006.gif[/IMG]


I'm **not** saying gFTP or any other linux ftp client is bad, I'm just saying they are not as feature rich, dynamic, or customizable as what modern day windows users are accustomed to.  Personally I don't like WS_FTP at all, then or now.

---

### Post by ad_267 on 2009-07-20
> **phazei said:**
> I tried to use Nautilus, then I could just edit the files out wright and it would be great.
If I type [ftp://ftp.site.com](ftp://ftp.site.com) it asks for the password, then says:
'Nautilus cannot handle "ftp" locations.'

If I click Places > Connect to Server, it says:
'Cannot display location "ftp://user@ftp.site.com/"
Operation unsupported'

Ubuntu 9.04

I just tried it myself and it works fine using both methods. I don't think I installed any extra packages, but I did a package search and it looks like you might need to install the libgnomevfs2-extra package. It looks like this doesn't support changing file permissions though, so that's probably a deal breaker.

Curlftpfs overcomes this but it looks like you need to issue a few commands to mount a remote location with it.

FireFTP is another possibility, it says it supports synchronization.

---

### Post by smartbei on 2009-07-20
Have you tried running them with Wine? WS_FTP has versions that are rated platinum, and CuteFTP is rated gold. (Platinum means it should work perfectly out of the box, gold means it should work fine with a little configuration). If this will solve your problem, who cares what operating system the application was written for?

---

### Post by dlmarti on 2009-07-20
I know slickedit does what your asking, but its not free.

I still like ncftpget/ncftpput, because I can put those into make files.

rdist will automatically upload changed files to the server.

tbh, nautilus is still the most seamless ftp client I've seen, at least for simple spot changes.

For larger changes I use Slickedit, or filezilla.

---

### Post by monraaf on 2009-07-20
> **phazei said:**
> 
I tried to use Nautilus, then I could just edit the files out wright and it would be great.
If I type [ftp://ftp.site.com](ftp://ftp.site.com) it asks for the password, then says:
'Nautilus cannot handle "ftp" locations.'

If I click Places > Connect to Server, it says:
'Cannot display location "ftp://user@ftp.site.com/"
Operation unsupported'

Ubuntu 9.04

If you are going for the GUI approach, that's indeed the way to go. Make sure you have libgnomevfs2-extra installed.

---

### Post by morningboat on 2009-07-20
CrossFTP is a powerful FTP client supporting multi-tabs and the remote site editing, but you need to pay for the Pro version. [http://www.crossftp.com](http://www.crossftp.com)
[IMG]http://www.crossftp.com/Screen_Client_Main_Linux.png[/IMG]

---

### Post by phazei on 2009-07-20
I have libgnomevfs2-extra installed.  I tried reinstalling it, no go.  Nothing in /var/log/messages or dmesg.  I suppose I should open a new thread under the support section for that.

I hadn't thought of Wine, I just assumed it wouldn't work well for anything that needed networking.  I guess I could use CuteFTP if I can't get Nautilus working.  Too bad SmartFTP is rated Garbage, I bought a license for that one.

I did look at the CrossFTP site.  It looks ok, I might try it.  SlickEdit seems like an entire IDE, but it looks pretty nice, though pricy.  I just checked and NetBeans PHP has [ftp support]("http://blogs.sun.com/netbeansphp/entry/ftp_support_added") as well.  So I can try that out as well.

Thanks for the good replies, first thing I need to do it fix Nautilus.

---

### Post by michaelzap on 2009-07-20
@phazei: I just wanted to chime in and say that I completely agree with you. I started using Ubuntu when Feisty came out, and I was really shocked that there doesn't seem to be an FTP app for Linux with the features that a Windows user can get from WS_FTP, WinSCP, and lots of other programs. It was especially surprising to me because in general there is such a wealth of excellent FOSS software for Linux, and I assumed that Linux users would see the value in a quality FTP client even more than other OS users.

I currently use FireFTP for basic operations and Filezilla for mass moves and whatnot. But I agree that Filezilla is nowhere near as feature-rich as what I was used to in Windows. Many of those features (tabs, directory monitoring, proper synchronized browsing) improve usability and work flow dramatically, and I really do miss them.

CrossFTP looks better than the (many) others I've tried for Linux, but I'd prefer a FOSS option.

---

