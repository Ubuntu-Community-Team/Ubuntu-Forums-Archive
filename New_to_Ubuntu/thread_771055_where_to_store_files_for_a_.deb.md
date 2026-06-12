---
title: "where to store files for a .deb"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by scragar on 2008-04-27
I'm planning to build myself a small .deb (or 3) for a few programs I've written over the course of my stay on ubuntu(starting with a small perl script which monitors Apache with quick key shortcuts to restart, stop, start apache, as well as options to veiw logs etc, then my new scraper script that monitors several external sites on given rules for changes, then updates an RSS feed acordingly, allowing you to subscribe to sites without RSS feeds normaly available, and finaly my middle of the road script, a small script to be installed, then run right after a fresh install, that provides options where defaults go, letting you uninstall programs you don't want and install programs you do want with minimal effort (all programs sorted by catagory, so there's browser, torrent, messengers, email, text editors, office software and video players) written in perl(with pgtk), although once it's done it offers to uninstall itself and clean up the install :P -- I love that feature)

And I was just wondering, where should I store files that are installed? I know config files need to go in the users home directory, and executables in /usr/bin , but what about other files?

---

### Post by kostkon on 2008-04-27
You can put them in */usr/share/app's folder*. e.g.. if your application is called app1, then put the rest of the files in
```
/usr/share/app1
```

---

### Post by Six_Digits on 2008-05-12
Can I have a copy of the last two scripts? Sounding pretty useful...

---

### Post by scragar on 2008-05-12
Will post them online somewhere once I get my net back up and running. The scraper is, unfortunatly, very hard to write custom rules for matching content (rule is same as grep for reading in a given value, then may then be resorted(for days in various formats), before appending a generic URL(actualy accepts something like: ```
http://www.nuklearpower.com/daily.php?date=**{$3}{$1}{$2}**
``` where $1 is first bracket in match...) and logging result to a xml(rss) file(which you add to your fave reader), by far not the most efficient script, however it's ram consumption is normaly limited to around 3MB (oh, and warning, the scraper is in PHP(apt-get install php5-cli = command line interface :P) because I got annoyed with perl not accpeting a pipe to grep...)).

---

### Post by Six_Digits on 2008-05-12
Sounds good, let me know :)

---

