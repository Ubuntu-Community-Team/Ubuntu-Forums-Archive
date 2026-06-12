---
title: "Noob bash script problem"
date: 2010-12-02
forum: Programming Talk
---

### Post by rbishop on 2010-12-02
I am definitely a noob when it comes to writing scripts and overall command line stuff, but I am working on that, so any help is greatly appreciated.  I have two scripts that are backing up my local server.  One is done on a nightly basis and the other is done on a weekly basis.  What I want is the Weekly one to email me once it is completed.  I have setup the script to burn to a DVD as you will see in the script.
```


TD=$(date '+%m-%d-%y')


##################################
##                              ##
## Copy files for weekly backup ##
##                              ##
##################################

cp -r /Shares/Files/Backups/* /weekly/
cp -r /Shares/Files/Misty-Backup/* /weekly/

##################################
##                              ##
##  Make ISO for Backup to Disc ##
##                              ##
##################################

mkisofs -o /$TD-backup.iso -r -J /weekly/

##################################
##                              ##
##       Burn ISO to Disc       ##
##                              ##
##################################

cdrecord -v -pad speed=2 dev=ATAPI:/dev/scd0 /$TD-backup.iso

##################################
##                              ##
##       Remove ISO image       ##
##                              ##
##################################

rm /$TD-backup.iso

##################################
##                              ##
##      Remove Weekly Files     ##
##                              ##
##################################

rm -fr /weekly/*





```

I am not looking for anything fancy in the email.  Just a basic..."this has completed" type email.  I do have the output going to a file also, so if I could either get that file attached as an attachment or the contents could go into the email body that would be good to.

---

### Post by r-senior on 2010-12-03
Are you running a local mail server? If you don't know, you probably aren't. Not the easiest things to configure. ;)

I'm no mail expert but in setting up webmin on my server I installed [msmtp]("http://msmtp.sourceforge.net/") to handle local status emails like this. It doesn't do local deliveries - it requires an external mail server that it routes through - but it is easy to configure and pretends to be sendmail.

Sending email from a script then becomes as simple as:

```
cat myfile.txt | msmtp -- myaddress@mydomain.com
```

or, if you want a standard subject line that's not in the file:

```

cat - myfile.txt << EOF | msmtp -- myaddress@mydomain.com
from: myserver@mydomain.com
subject: Yet another log file

EOF
``` 

Someone else will have a neater solution but I find msmtp works well and interfaces with things that expect sendmail, e.g. webmin, mdadm.

---

### Post by rbishop on 2010-12-03
Thanks for the reply R-Senior.  I will look into msmtp.  definitely seems like it is what I am looking for, especially for the home server.  No I am not running an email server at the house, way to much configuration work for something I regularly rebuild....(just for fun LOL).  

If anybody else has a suggestion please keep them coming.

Thanks

---

### Post by roccivic on 2010-12-03
I don't have anything email related for you, but may I suggest swapping

```
cdrecord -v -pad speed=2 dev=ATAPI:/dev/scd0 /$TD-backup.iso

##################################
##                              ##
##       Remove ISO image       ##
##                              ##
##################################

rm /$TD-backup.iso

```

for 

```
cdrecord -v -pad speed=2 dev=ATAPI:/dev/scd0 /$TD-backup.iso && rm /$TD-backup.iso
```

So that, if the cd recording program fails to burn your cd, you will still be left with an iso image (just in case).

You should also check that the newly created image is not too big for your media. No point in trying to burn 1G on a 700MB cd.

Peace

---

