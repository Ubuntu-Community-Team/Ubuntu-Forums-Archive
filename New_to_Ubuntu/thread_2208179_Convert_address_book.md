---
title: "Convert address book"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by squakie on 2014-02-26
I have a Juno address book (.nv) that I need to convert to another mail client.  It needs to be in vcard or csv so I can import it to my brother in-laws gmail account as he is having problems with Juno.  Found out how to move the email over to online gmail, now need the address book.

I found a program called "Dawn" to do so, but the latest release was a beta in 2006 - I grabbed the release prior to that.  It does run in Wine with the same results as in Windows.

Here's the problem I'm having:

It opens the .nv file fine and shows the contacts and groups fine in it's window.  However, when I do a "save" and either of the 2 types mentioned above there is only 1 contact in the output file.  I tried the "L" something format as well and get nothing into gmail's contacts.  I didn't check the "L" something file, only the csv and vcard output files and both only show 1 contact.

Has anyone used this program and if so do you have any idea what I might be doing wrong?

Does anyone know of any other tools for Linux or Windows that can process a Juno .nv address book file and output csv or vcard?

Thanks!

EDIT:  BTW - I did try 2vcard in the repositories because it said it supports Juno.  However, when I run it with the -f juno option it gives no errors but the output file is empty.

---

### Post by squakie on 2014-02-27
So far no luck.  I am currently working on a C program to try to do this, but I have pretty much forgotten all of my C from days past.  It will be a command line only program to start - may add a GTK interface later, taking infile, outfile and outfile type (currently I'm thinking CSV and VCARD, as I'm hoping I can find descriptions of both).  Don't have a clue how to handle mailing lists that are in the file so for now they'll just be overlooded. 

If I can get the basics of this going, I can post the source for others to use or work on if they want to - perhaps to include other outfile types.

If kept as a command line program it will run in Ubuntu but should also, with recompilation, run in Windows as well.  Even if I add GTK it could still be cross-platform.  So I'm hoping it's simple enough not warrant too much - especially considering my C skill set now versus the past.  Probably even easier in C++, but I don't know it anymore at all.  While I was working I took some classes in it and wrote a few programs, but that was about 20 years ago now, and I don't remember things that long ;)

---

### Post by mips on 2014-02-27
Does Juno not have a export to csv feature?

Could you provide me with a sample of the .nv file by any chance via PM, feel free to edit sensitive info.

---

### Post by squakie on 2014-02-27
The only one for Linux that was supposed to work was 2vcard, but it didn't output anything.  I've also been running Dawn in Wine but only get 1 line of output.

Simplest form of output from the .nv file, not including the groups:

```
Type:Version 
Version:AB 0.3.0 
 
Type:Entry 
Email:me@me.com
Alias: 
Name:last,first
Primary Phone: 
Birth: 
Address: 
Deleted:0 
Time:1300446059 
 
Type:Entry 
Email:minime@gmail.com 
Alias: 
Name:Me,Mini
Primary Phone: 
Birth: 
Address: 
Deleted:0 
Time:1300274685 
 

```

I'm in the process right now, and will continue until I'm done, of writing a C program to parse everything before the ":" and call a funtion based on that.  When I hit a "Time" I will construct the output - I'm just looking at cvs and vcard right now - and write it to a file.  The file it creates I want to be able to import to online gmail.

I'm already off to a good start.  I thought about using the shell, but there are somethings that get a little complex - stroing the values, writing out the proper format, processing groups, etc., I just don't see being an easy execrsize in the shell, so I chose C.  I should pretty much be done later Thursday.  It's getting late now (4:45 a.m.) so I'm heading off to bed.

---

### Post by squakie on 2014-03-01
I didn't know where else to post this.

I have written a C program to process a Juno address book in .nv format and convert it for import to gmail's contacts.  It is not all inclusive, as all that get's processed at this time is:

   - first name
   - last name
   - birthday
   - phone
   - alias
   - email

The only things actually output to the gmail formatted CSV file are:

  - the last name 
  - the first name
  - the email address

In addition, my gmail contacts main page is only showing the last name and the email address, so the last name that is output is actually the last name followed by a space followed by the first name.  In this way, instead of just saying "Doe"  it wil say "Doe John".

Currently the only supported output is for a CSV file for use for importing into gmail contacts.

There are "hooks" in the program that can easily be added to process more of the input data if needed.  In addition, it should be a relatively simple matter to create outputs for other email clients' address books  by just parsing out the correct output type and adding the appropriate coding (would be similar to what's in the gmail output code).

At any rate, I'm not a good programmer, so the code doesn't look pretty, but for my use it works, and it can be changed as needed.

So.........if anyone would like a copy, or would like to take the code and expand it do more, just let me know.  I don't "own" it - it's free as far as I'm concerned for anyone.

---

### Post by squakie on 2014-03-01
Got a rudimentary program done for what I needed to do.  Obviously it can be modified.  Program is free if anyone wants it and maybe wants to expand it.

BTW - the program is in C and is command line based.  I wrote it and used in in Ubuntu.

---

### Post by squakie on 2014-03-01
For those who may wondering:  this is for my brother in-law, after his Juno email running locally won't start anymore.  Gives a message about checking the email directories or some such thing and then hangs.  Tried other solutions for externally "fixing" the Juno database - they didn't help.  So, with no way to get into Juno to see if it even supports and export, I needed a way outside of Juno to read it's address book.  Hence the need for my program.

---

### Post by sudodus on 2014-03-01
I don't need it now, but sometimes I help people migrate from Windows, so I can see where your program can be used, either as is or as a template for similar conversions of email address books.

So please publish the source code in this thread as an attached compressed file along with the md5sum :-)

---

### Post by squakie on 2014-03-02
It works to create csv format for loading in to Thunderbird now as well.  Obviously I am only picking up the few fields that showed in my brother in-laws juno address book, but the code is easily enough changed.

BTW - I found out why I couldn't get strings working and instead used statements to copy memory (memset in C) - I never allocated memory for the strings!  So, it works the way it is, but could be made much simpler if someone wants to take the time to change everything to strings, instead of character arrays.  Sorry about that - I'm pretty much starting over when it comes do coding now. ;)

Also - can you tell me how to create a md5sum, and I assume on the compressed file?

---

### Post by squakie on 2014-03-02
OK, I *think* I have it:

The attachment should be the source.

The md5sum:

dddc78c8d3feb41ed385a1d329a060b2  nvconvert.c.gz


This code can just be run straight in Ubuntu after compilation.  The source address book - currently just Juno - is currently "parsed" by stripping off the 2 trailing characters.  This is because the Juno address book comes from Windows so it has CR/LF at the end of each line.  If the truth be told, there should be a small funtion to strip off any trailing character(s) that might be end-of-line character(s) so that it would work no matter where the source.  Those characters I assuming could be stored in a string and the a funtion just start at end of line and wok backwards, putting a null in the place of each of those characters found.  I might work on this part and post a new source afterwards.

For now, things are  a starting point.

Please check the end of this thread for the most current version.

---

### Post by sudodus on 2014-03-03
Thank you for sharing :KS

---

### Post by squakie on 2014-03-03
I'll be posting some revised code in a day or 2.  Found out what I was doing wrong with strings, so I need to change that all to work with strings now.  Also, I'm adding another command line parameter for input type - that way the "hook" is there for adding more. ;)

Sorry for such crappy code!

---

### Post by squakie on 2014-03-07
> **mips said:**
> Does Juno not have a export to csv feature?

Could you provide me with a sample of the .nv file by any chance via PM, feel free to edit sensitive info.

Sorry - I've been bouncing around on several things, so I completely missed this post I think.

It's possible Juno has an export (they don't online), but when you can't start your Juno it makes it a little hard to find out ;)

Thanks!
Dave

---

### Post by squakie on 2014-03-07
I marked this thread as unsolved again for 2 reasons:

(1) Some VERY patient people on the Programming forum have helped me straighten out some of my unbelievably crappy code - it actually looks more like a program now ;)

(2) I'm going to be adding support for Yahoo! online email CSV format shortly.  I exported my address book on Yahoo! so I have the format now.

That will make 3 "output" formats suported - Gmail, Thunderbird and Yahoo!.  Keep in mind the Juno address book I've been working with has very limited data so there are only a few known things to parse from it for now.  If people find more, or if someone starts pulling apart another address book, obviously the code will need to change - it will be easier now ;)

So, I'm just lkeeping this open so I can post my next version, and perhaps leaving it open after that so that if I need to make further changes or someone adds things that the revised code can be posted here as well.

---

### Post by squakie on 2014-03-07
Just thought of something:  Since I already know the csv formats for Gmail, Thunderbird and Yahoo!, there wouldn't be much to converting from one csv format to another - say Gmail to Thunderbird, etc..

After I get things settled in for Yahoo!, I'll post the newest code here and then go back and look into that.

---

### Post by squakie on 2014-03-09
Okay, here's the latest.  Notice the name change to abookconvert.c, reflecting that it will in the near future read more than just Juno input.

This version:

- the code looks more like C code should, rather than the mess I had the first time around ;)

- can only process Juno address books in .nv format

- can generate csv files for:
[LIST]
[*]Gmail 
[*]Thunderbird 
[*]Yahoo! online email contacts 
[/LIST]

After the file is generated you can just import the file.

Again, since only a few tags for the Juno address book showed in the input I'm using, very few of them get processed.  If you find other tags, please post back a sample of Tag:value so I can update the program.

Quite possible you may find bugs in the output - if so, please let me know! ;)

So, the attachment is the source code.

The md5sum for the gzipped file:```
cc0384efcae1d6d9787c10ba4864841a  abookconvert.c.gz
```

Dave ;)

---

### Post by sudodus on 2014-03-09
Thanks again for sharing :-)

I had a quick look at the code, and it look quite well organized now.

-o-

A quick comment about another mail address format, that might be urgent to export soon:

Windows XP will reach end of life in April. I think many people have Outlook pst files containing address lists (and mails). It is possible to export the information as csv files as long as XP is running ...

---

### Post by squakie on 2014-03-09
> **sudodus said:**
> Thanks again for sharing :-)

I had a quick look at the code, and it look quite well organized now.

-o-

A quick comment about another mail address format, that might be urgent to export soon:

Windows XP will reach end of life in April. I think many people have Outlook pst files containing address lists (and mails). It is possible to export the information as csv files as long as XP is running ...

if you can get me a sample csv file, I'll do my best.  All i ned is the "header" from up front that shows the field names and the comma separators, and perhaps just 1 test entry with it.

Never thought about that, and I could get on it right away.  I have asmall dual-boot xp partition but don't use it anymore.  I can check and see if it has outlook - but if it does I'm sure it will only be outlook express, but that would be a start.

Thanks!
Dave ;)

---

### Post by squakie on 2014-03-09
I just fired up XP (the last time I used it was just to convert my brother in-law's actual Juno email minus groups).   I did find "Address Book" in the menus so I put a full test entry in there and exported it to csv.  I'll get started on that tonigth as I imagine there will be people with that as well, and hopefully the Outlook address book isn't too different from that.

Dave

---

### Post by sudodus on 2014-03-10
I made an ods file for LibreOffice Calc from your and my friend's corresponding contact lists. It can be public so I attached it to this post.

I think the order can vary a lot for the posts between locales, probably also between versions. I think the converter cannot rely on the order, but must use the headers (column headers in the first line) to identify the items more or less independently of the source.

For one-off purposes, it might work to do it manually in a spreadsheet. It would certainly be nice to have a well debugged program, that can do it automatically, unless the receiving program or utility has such a tool already. I think you should check for that before you spend too much time programming. But if you enjoy it and have the time, then do it, even if it is not necessary :-)

---

### Post by squakie on 2014-03-10
You know, I'd LOVE to continue on....."but".......Since not working since 1996, even though I was a systems programmer and sys admin on everything from big boat anchor pieces of iron down to micros, I've lost everything since then.  I feel embarrased with my lack of C knowledge now.  I guess close to 20 years with no use it just goes away - certainly not like riding a bike ! ;)  Same with networking - used to be old hat, now I'm just a disaster waiting to happen.

So......I think I'll just stop with what I needed for now - the ability to convert the juno address book.  I'd really love to continue, and I see in my head what I have to do, but I just don't remember the programming enough anymore to make it happen.  Maybe because it's a "what the heck" thing now versus an absolute for work.

So, thanks for the input and the ideas - it just my lack of programming skills now that makes me have to stop.  I think the guys in the Programming forum where pretty tired of me already! :)

---

### Post by sudodus on 2014-03-12
I see. Well, once the data format is CSV, it can be managed by simple tools like spread-sheets.

---

### Post by squakie on 2014-03-12
Thanks for understanding - I make myself kind of mad when in my head I still know exactly what to do, but all of my tech programming background has gone to heck!  Sometimes I think paying for that college eduction has really paid off later in life!  ;) ;)

At least if anyone is looking for a tool to just convert a simple Juno .nv address book, this will convert to CSV files for Gmail, Thunderbird and Yahoo.  Not much, and makes for a very isolated thing.  Oh well......

---

### Post by squakie on 2014-03-18
Something I did learn playing around with all of this:  a lot of the address books will import the CSV exported file from another with no problem.  There are sometimes fields that aren't matched up, or might get truncated, etc., but for most simple address books it works pretty close.

---

### Post by Johnny_Harris on 2014-06-12
Hi, I have the same problem with needing to convert Juno NV file to CSV.  My firend has 1200 contacts in there and it needs to be uploaded to Gmail.  I am not a programmer and do not know how to open the program. Can you help me?

---

### Post by squakie on 2014-06-29
> **Johnny_Harris said:**
> Hi, I have the same problem with needing to convert Juno NV file to CSV.  My firend has 1200 contacts in there and it needs to be uploaded to Gmail.  I am not a programmer and do not know how to open the program. Can you help me?

After your last PM I had a look at the snipet of the .nv file.  It contains a "Work Address:" record, which requires a lot of parsing down to it distinct fields.  The program (download via the attachment in post #16 of this thread) currently does not do that.  You've offered me money, but I have no interest in that - the program is to remain free.  It has also long-since served the purpose that I needed and wrote the code for in the first place.

My suggestion?  

(1) Download the source via the attachment in post #16 of this thread

(2) Take that code, and the snipet of the .nv file like you sent me, to someone who is versed in C programming in Linux.  The code is laid out such that it isn't hard to add that in, but it also requires parsing on double "^" and the program currently only parses at a single character.

The peron who modifies the code for you also needs to be aware that it doesn't look at first glance that gmail supports work data.  Thunderbird does, and it appears yahoo does as well.

The single most important thing:  the modified source MUST be  posted back here, and the code MUST remain free.  It's between you and that person if you pay them for the work  but since it is my code, I require that the modified source be posted here in an  attachment and the code MUST remain free open-source.  Not adhering to those rules is prohibited.  I think that falls under 1 of the open source licenses.

---

