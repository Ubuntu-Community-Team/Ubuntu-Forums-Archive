---
title: "Automate FTP"
date: 2010-02-01
forum: Programming Talk
---

### Post by jtrulen on 2010-02-01
Greetings,

In one of my projects, I have to do an automated FTP from Ubuntu to a windows machine. However the problem becomes that I do not know how to do this.

Would anyone be able to help me through this?

Thank you,

Jordan Trulen

---

### Post by Hellkeepa on 2010-02-01
HELLo!

Sounds like you're out to get [Dropbox](https://www.dropbox.com/)-like functionality..? If not, then please explain what you're after in more detail.

Happy codin'!

---

### Post by jtrulen on 2010-02-01
That would work, however it is extreme overkill for what I need.

I have a php script that writes data from a database to a file. That file needs to be transferred to the windows server once every week. The file in question is no more than 5 kb in size, so I think that would be overkill to use dropbox for. The file is only a single column, and anywhere between 1 and 500 entries long.

---

### Post by Hellkeepa on 2010-02-01
HELLo!

Ah, I see. I'd set up a crontab for this, using the CLI FTP client. "man crontab" for information on how to set it up, and "crontab -e" to edit the crontab file. The ftp client should be self-explanatory, but "man ftp" gives you all the details you need.

Happy codin'!

---

### Post by jtrulen on 2010-02-23
I know it's been awhile, I've been busy.

So I can do the commands manually, but I'd like to set them up in a file and set that file to run automatically.

How do I go about doing this.

I know that I will need:

ftp [ host ]

but after that, it just sits there waiting for the user to put something in even though in the file, I specify the username and password.

Any ideas?

My file looks something like this:

```

ftp [host]

[username]

[password]

put [local-path] [host-path]

close

exit

```

---

### Post by jtrulen on 2010-03-09
No ideas anyone?

---

### Post by myrtle1908 on 2010-03-09
Use the Perl Net::FTP module.  Problem solved.

[http://perldoc.perl.org/Net/FTP.html](http://perldoc.perl.org/Net/FTP.html)

---

### Post by jtrulen on 2010-03-12
Alright, so now how about using the built in FTP in Ubuntu?

---

### Post by Hellkeepa on 2010-03-12
HELLo!

Ah, I was thinking about "sftp". That's scriptable, unlike the standard "ftp" client. Sorry about that mixup, though I'd advice you to use "sftp" anyway. FTP transmits everything in cleartext, including passwords, after all. While SFTP goes via SSH, so it's not only safer, but also doesn't require an FTP server to be installed. ;-)

Happy codin'!

---

### Post by memilanuk on 2010-03-12
Disclaimer:  I haven't tried doing what you're working at, not specifically.  That said... there are some CLI utilites that are designed to run non-interactively to upload, download, etc. HTTP< FTP, and such.

Here are the links to the Ubuntu man pages for:

[curl]("http://manpages.ubuntu.com/manpages/karmic/en/man1/curl.1.html")

[wget]("http://manpages.ubuntu.com/manpages/karmic/en/man1/wget.1.html")

Like I said, I haven't done what you're looking to do, but I think these should work fine.  I haven't used either one in a looooong time, but the man pages are pretty well documented and I imagine they have't changed much since I last used them.  I'd suggest testing until you have the complete syntax with all the parameters and flags worked out the way you want, then stick that command inside a bash script file and chmod it to make it executable, and run it from cron as needed.

HTH,

Monte

---

