---
title: "Installing applications - Esp MySQL"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by trek186 on 2012-10-11
Hello again everyone.  I have Ubuntu up and running.  Yay!  It's pretty and shiny.  The ADD kid in me likes that.

Next order of business it to get some software loaded.  I have quickly found out that installing applications is *very* different from clicking on an EXE in Windows.

I downloaded the [Processing]("http://processing.org/") programming software and followed their linux install instructions to unpack the files from the tar.gz file I downloaded.  Ok, great.  I found *a file* (a binary I think?) inside the unpacked folder which launches the application.  I have since made a short-cut to it, so I can open it.

Next I tried doing the exact same thing for the tar which MySQL came in.  I unpacked the folders, but that's about it.  I have no clue how to actually run it.  I attempted to run some of the terminal commands which a few websites said I needed to properly install MySQL, but I don't think they really did anything.  Other guides mention nothing about a .tar download, instead they talk about using the sudo apt-get commands to download MySQL via the terminal window.  At this point I am extremely confused.

So to boil my issues down:
1) Do I need to do something extra to fully install Processing and MySQL, since neither application appears in the spiffy launcher menus (or dashboard, or whatever its called - its the start-menu like thing)?
2) What is the *right* way to install MySQL (or any app for that matter without screwing it up?  Do I download a .tar file and hope for the best, or do I use sudo apt-get in the terminal window to download it?
3) Is there such a thing as a good tasting low-fat salad dressing?

---

### Post by zhogan85 on 2012-10-11
1) I can't speak to processing, but for MySQL, to install, open up a terminal and type
```
sudo apt-get install mysql-server
```
This should start the install process for MySQL.

2) Generally ,the correct way to install software that is in Ubuntu's software repositories is using apt-get

```
sudo apt-get install [program_name]
```

If you're not sure exactly what the program is called, use 

```
sudo apt-cache search [term]
```

and it will return available software containing the search term in their name.

If the software is not in the repositories, that's when you start having to deal with compiling yourself or using a ppa, but there is a lot of software available, so you should be pretty set.

3) No, you'll just have to deal.

Cheers!

---

### Post by trek186 on 2012-10-11
Oooh!  Awesome!  Thankyouthankyouthankyou!  I know what I'm doing tonight!

---

### Post by zhogan85 on 2012-10-11
> **trek186 said:**
> Oooh!  Awesome!  Thankyouthankyouthankyou!  I know what I'm doing tonight!

Hehe, I know too, eating salad with full fat dressing!

Also, if this gets you sorted out, please don't forget to mark this thread SOLVED.

---

### Post by trek186 on 2012-10-11
Ok, tried all of that, including the "sudo apt-get install mysql-server"  command you listed above.  When I used "sudo apt-get install mysql" or  "sudo apt-get install processing" (or variations involving the exact  folder names which were generated when I unpacked the tar files), I  received messages saying
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package [search term]"
Do I need to specify a file path when I use "sudo apt-get install"?

When  I ran the "sudo apt-get mysql-server" command the terminal window did a  bunch of web queries and downloads, but nothing related to SQL is  showing up in the dashboard...

---

### Post by zhogan85 on 2012-10-11
For processing,  that's because its not in the repos but i thought you said you installed it already. For MySQL,  open a terminal and type MySQL.

---

### Post by trek186 on 2012-10-11
Ok, that was weird.  The ubuntu software center says MySQL Server is installed, but I can't find any links to the program in the dashboard.  Odd.

I realized that I could install MySQL through the software center, and I opted to go that route.  Now to figure out how to properly configure Processing...

---

### Post by trek186 on 2012-10-11
> **zhogan85 said:**
> For processing,  that's because its not in the repos but i thought you said you installed it already. For MySQL,  open a terminal and type MySQL.

Not really...  I found a file in the extracted tar files which launches what looks like the entire compiler.  I'm just afraid that I didn't install it "the right way".  I don't want to crash my code or anything once I start programming. :)

---

### Post by zhogan85 on 2012-10-11
OK, sounds good, and good luck configuring processing. If your not sure you installed it correctly, google installing from source in ubuntu, there is plenty of documentation.

Cheers!

---

