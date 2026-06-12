---
title: "Perl CD Archive"
date: 2006-08-26
forum: Programming Talk
---

### Post by Pontifex on 2006-08-26
I've been doing some coding lately in Perl and I'm trying to find out how to do something new.

Some background.  I've been cataloging my (very large) data CD archive with a shareware Windows program for some years now.  The company has since gone out of business, but I've been able to hack something together so the awful thing will work under Wine.  This works “okay”.  It crashes a lot and doesn't work right.  But at least I've had access to database.  It would be prohibitive to change archival methods at this point.

So I've been looking for a way, a series of steps really, that I could implement to migrate my database over to something more modern.  The ideal is to put everything in a little MySQL database for quick searches and what not.  But I don't have the time, what with graduating soon, to sit down and get everything working in a couple of days.  So I'm going to start small.

The output format for the records of my current database are text files.  Pretty simple ones at that.  Here's a sample:

```

[Info]

DriveType=5

ImagePath=F:

Volume=NEW

Serial=4206721414

FAT=CDFS

DiskSize=699441152

DiskFree=0



[Comment]

0=Catalog Created at:

1=7/22/2003 6:30:31 PM

2=

3=Catalog Mode:

4=Folders&Files

5=

6=http://www.historyplace.com/

7=worldwar2/riseofhitler/named.htm



[F:]

CD catalog 072203.htm=8040200

CD_Catalog_Expert_v8.00.zip=10695

New Text Document.txt=60

Virgins hymen.mpg=10882552

X-Men - 315 - The Dark Phoenix Saga Part 4 - The Fate of the.avi=64677888

X-Men - 319 - Weapon X, Lies and Video Tape.avi=65654784

X-Men - 401 - Courage.avi=65697792

X-Men - 403 - Proteus part 2.avi=53217280

X-Men - 405 - One Man's Worth Part 2.avi=60475392

X-Men - 406 - Beyond Good & Evil 1 - The End of Time.avi=84883456

X-Men - 407 - Beyond Good and Evil Part 2 - Promise of Apoca.avi=81629184

X-Men - 408 - Beyond Good and Evil Part 3 - The Lazarus Cham.avi=80496640

X-men - 402 - Proteus, Part 1.avi=60407808

X-men - 404 - One Man's Worth (Part 1).avi=60479488



[F:\cdc]

FILE_ID.DIZ=254

HISTORY.TXT=3966

License.txt=2279

Order.txt=3349

README.TXT=6283

pad_file.xml=6485

setup.exe=949357


```

It looks pretty straightforward.  I need to access the CDrom for some basic information: size, path, CD name, etc; and print at the top under the “info” header.  Then take the sizes of the various contents and print it next to relevant TOC entry.  It doesn't seem that hard on the surface.  Though I'll probably leave out that comment section, odd stuff in there.

My choice for this project is Perl, because I'm familiar with it and it seems to be a popular choice for all  the other custom GNU CD cataloging scripts out there; what little there are.  I can probably hack something together to check if the CD is mounted, by examining the output of 'df', and to try to mount the volume, with 'mnt', but it seems like there should be a better way.  I assumed, when I started, that there would be a Perl module that would make my life easier; but searching google and the forums here doesn't show anything related to what I'm looking for.

So really I'm asking for input or strategies that would make this little project easier.  Also I'd like to preserve the archive format, as shown above, for backwards compatibility; until I move on to some more robust database.

---

### Post by JonahRowley on 2006-08-26
A MySQL database would be easy to set up.  A disc table not much more than id and name (or just id) to act as a foreign key.  An info table with disc_id foreign key column and all the columns in the info section.  Same for all the other sections.  It should be a very simple script to import the data into the database.  Perl I know has ini parsers, so that work is done for you.

Only obstacle is F:, F:\cdc, etc.  Maybe a files table with disc_id, path (which will be /, /cdc, etc) and filename.  I don't know why they'd keep the CDROM drive letter in there, what if you have more than one drive?

Overall, this is an easy project.  Some interface (command-line, GUI or web) to query this data would be trivial as well.

X-men and porno?  Nice combination.

---

### Post by Pontifex on 2006-08-28
Though I like your avatar, I have to make issue with the things you replied with.

My aim here is not to setup a MySQL database.  I don't want to touch it.  I don't want to even think about doing it.  Not with my class load and responsibilities this semester.  I want to program something simple and straightforward that will allow me to continue to catalog while I'm going to school.  

See that?  Simple.  Something I can program in a day and pick up my back log of archivable DVDs without having to install, diagnose, troubleshoot, do voodoo rituals over, make blood sacrifices to, etc; a MySQL database.  Forgive the hyperbole, but I know I'll be back here with a more complex set of problems if I even touch a SQL database while trying to do everything else.

So again, with Perl, how do I get the TOC, the title and size of files from a disk in my optical drive?

Pontifex

---

### Post by Rasitiln on 2006-08-29
Look into hashes and arrays. I can't tell you how it could be done but I'm fairly certain it would be done using one of the two if not both.

---

### Post by Pontifex on 2006-08-29
Well yes, I was assuming a data structure would be involved somehow.

Pontifex

---

### Post by Pontifex on 2006-09-04
Huh.  Nothing.  Does this mean that there's *no way* to access a CD drive via Perl?  I'm beginning to think so.

Of course searching google, CPAN and these fine forums has produced nothing; so I'm probably not going to find an answer.  Ah well.  I'll just post some bash quotes to keep the thread alive a bit longer.

---

