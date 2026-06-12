---
title: "software installation/ compiling using make"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by cdlam on 2012-09-18
Hey, not sure if this should go here (because I am an absolute beginner) or in the Compiling Programs thread but here goes...

So I need to use this software called PASA (program to assemble spliced alignments, [http://pasa.sourceforge.net/#A_sii](http://pasa.sourceforge.net/#A_sii)) for a research project and it requires unix, so I installed ubuntu on my laptop. Anyway, it gives instructions on how to install the program:

"Move the PASA distribution to a location on your filesystem that we can call PASAHOME, such as /usr/local/bin/PASA. From henceforth, we'll refer to this location as $PASAHOME.

Build the components of PASA that require compilation by running:

make

in the $PASAHOME directory. This will build the utilities: pasa, slclust, cdbyank, and cdbfasta, and place them in the $PASAHOME/bin directory."

Ok, so basically I've learned how to move around directories....and that's about it. I don't even know how to run the make command, I just keep getting different errors (Like, "nothing to do with ___. Stop.")

So could anyone point me in the right direction? Thanks

---

### Post by drmrgd on 2012-09-18
Looks like you have a bit of an uphill battle on your hands as there's a lot to installing this program.  First, be sure to install the prerequisite programs that the installation instructions indicate are necessary, mysql, cpan, the cpan module DBD::mysql, GMAP, and FASTA.  

I'm not a mysql expert by any stretch, and so I'm not 100% sure how to install and configure it.  There are a number of mysql packages in the repositories, and I'm not sure whether you need the full server install or just the client install.  That might be a question for the PASA forums.

I believe that CPAN is already installed by default (I'm not 100% sure on this).  You can check by just typing 'cpan' in a terminal window.  You might be asked to set up a bunch of defaults first, and I think the default answers are fine.  Once it's set up, as the instructions indicate, close your terminal window and open a brand new on to allow the program to fully configure.  Once it's set up, type cpan again, and when the program loads, run:

```
install DBD::mysql
```

Assuming everything is correct, it should add that module and you'll be good to go.

For the GMAP program, you can follow the instructions on the page linked from the PASA site.  Alternatively, there is a version in the repositories, which you can get by running:

```
sudo apt-get install gmap
```

It's an older version, and I'm not sure if it's fully compatible with the latest version of PASA.  It's easy to try, though. 

For FASTA, click the link provided to download the installation.  Once you've got it, unpack it and have a look at the README file.  You'll find instructions on how to install that package.

Once you've gotten that far, you should be good to install PASA.  Put the uncompressed folder into the location you want it to reside (/usr/local/bin as suggested is OK):

```
tar xvfz PASA_r2012-06-25.tgz && sudo mv PASA_r2012-06-25 /usr/local/bin/PASA
```

Then navigate to the folder and simply type 'make'.  If everything went OK, you will see it complete and there will be no errors listed.  If not, post the errors you get here and we *might* be able to help.  The package is quite complex and specific.  So, you might do better getting some advice from the PASA forums for really specific things, assuming the forum is still active.

I hope that helps.  If you have more questions just ask.  Like I said, for a new person to the CLI, this is a bit of a task, which is going to require some effort.  You should be able to learn alot from the experience, though!

---

### Post by cdlam on 2012-09-21
Hey thanks for the post, yeah this is going to be difficult but I think I can get it going. I'm working on getting Mysql set up which has been kind of confusing. Cpan IS already installed, I just went with the default options for now. If I have any issues I'll let you know. 

...

I'm sure there will be issues haha. Thanks again for the help.

---

### Post by drmrgd on 2012-09-21
Yes, the mysql part is the only one that I'm not sure of at all as I don't know it at all, and anytime that I've spent a second looking at it, I realized it's a bit of a beast.  I think once you get that set up, you'll find the rest goes pretty smoothly.  Definitely post back if you have any issues!

---

### Post by cdlam on 2012-09-24
FINALLY got DBD::mysql installed. It was a huge pain. So many errors, the documentation is very confusing but I persevered lol.

GMAP is also installed. I'm about to start installing the FASTA program. I did have a question about this:

"The utilities provided by each software package above should be available via your PATH setting."

This is from the PASA webpage, underneath where it talks about installing mysql, dbd::mysql, gmap, and fasta.

What is a PATH setting?

---

### Post by cdlam on 2012-09-24
Ah, and I've already hit a snag in the installation of FASTA. So the readme has this to say about installation:

> To make the standard FASTA programs:

   cd src
   make -f ../make/Makefile.linux_sse2 all

where "../make/Makefile.linux_sse2" is the appropriate file for your system. 

The executable programs will then be found in ../bin
(e.g. ../bin/fasta35_t, etc.)

For a simple test of a program, try (from the src directory)

   ../bin/fasta35 -q ../seq/mgstm1.aa ../seq/prot_test.lseg     

There are no makefiles in the src directory, they're all in the "make" directory. So in this directory I tried:

make -f Makefile.linux64

and get this error:

chris@ubuntu:~/Downloads/fasta-35.4.12/make$ make -f Makefile.linux64 all
make: *** No rule to make target `comp_lib2.c', needed by `comp_mlib2.o'.  Stop.

Any ideas?

---

### Post by drmrgd on 2012-09-24
Yeah, from the README, I think you have to explicitly follow what they say.  It is true that the makefiles are located in the 'make' directory.  However, there must be something in the way it needs to compile to have you run the command from the 'src' directory.  I'm not entirely sure.  It will compile if you go into the 'src' directory and run the command they suggest.   I did get a bunch of warnings after compiling it.  But, when I run the suggested test, it seems to work OK as far as I can tell.

Try it again from the src directory (and following the compile instructions explicitly), and see what happens from there.  Looks like you're almost there!

---

### Post by cdlam on 2012-09-24
Thank god for thread subscribing haha.

Ok, I literally copied that line from the readme and ran that, and a bunch of stuff happened and ended with the warnings you mentioned.

How exactly do you run those tests? Because I when I type FASTA or fasta nothing is found, and the bin directory is empty.

Thanks!

---

### Post by drmrgd on 2012-09-24
> **cdlam said:**
> Thank god for thread subscribing haha.

Ok, I literally copied that line from the readme and ran that, and a bunch of stuff happened and ended with the warnings you mentioned.

How exactly do you run those tests? Because I when I type FASTA or fasta nothing is found, and the bin directory is empty.

Thanks!

Have a look in the README in the main directory.  From that file, the instructions are:

```
../bin/fasta35 -q ../seq/mgstm1.aa ../seq/prot_test.lseg
```

You may have to play with the first bit of it depending on where you are in the file system at the moment (when I ran it I happened to be in the bin directory, so I just ran './fasta35' instead).

---

### Post by cdlam on 2012-09-24
Ok. I tried the test, and it did prompt it to tell me to input a sequence file, but then couldn't open the library for that file. But I guess that means the program is installed. So do you think that I can try installing PASA now, or should I try and figure out what's up with the test thing? Thanks again for all your help. Also, don't feel obligated to respond quickly or anything, I'm doing my senior thesis which basically means I'm always at my research cubicle on my computer lol.

---

### Post by drmrgd on 2012-09-24
No problem at all.  You just happen to catch me when I'm online and able to answer a few questions.  This tool looks intriguing to me anyway, and I may try to install it for myself in the future just to play around.

It looks like all of the dependencies are met.  From the Sourceforge page, "The utilities provided by each software package above should be available via your PATH setting."  This will be important as PASA is going to be looking for the binaries for each of these tools, and needs to know where to look.  By default, most programs use the PATH variable, since it's the easiest.  I think that some of your stuff may not be installed in folders that are part of your PATH.  I know for sure that you installed the FASTA program in ~/Downloads, which is not part of the PATH.  There's a few ways to go about this.  To see what's listed in PATH, you can run:

```
echo $PATH
```

You'll probably get a string that's something like

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Those are all the places in the system where the program will look for the binaries.  Likely the MySQL stuff is OK.  I'm not sure about GMAP, though.  What I would do (not that this is the best way, but maybe at least the easiest) is to create a folder for this stuff (like ~/bioninformatics) and put the whole FASTA folder in there.  Do the same with GMAP if need be.  Then you can add the bin folders as part of your path by editing your .bashrc file, a hidden file in your home directory.  So, let's say that you put the fasta folder in ~/bioinformatics, you could do this:

```
nano ~/.bashrc
```

Then, in the editor, add the following:

```
PATH=$PATH:/home/<user>/bioinformatics/fasta/bin
```

Be sure to change that line to match the real case (i.e. you user name, and the correct fasta folder name).  Then close and save the file.  Finally, you can log out and log back in, or just simply reload your .bashrc file:

```
source ~/.bashrc
```

After that, when you run 'echo $PATH' you should see the new location in the string.  This will mean that you can type fasta35 anywhere in the system and it'll run.  That will also mean that PASA knows where to look for it now.

If you get all that working OK, then you're pretty much ready to follow the rest of the instructions to build PASA and set up the configuration file.  If you get an error while running make in PASA, take note of what the error it.  Nine times out of 10 it's because it can't find a file, library, or program that's needed, and you'll have to install whatever's missing.  Post back any errors, though, and maybe we can help sort it out.

---

### Post by cdlam on 2012-09-25
Ok, well I didn't run into any problems when I ran make. The next part, about the pasa_config and conf.txt I'm confused about. There is no conf.txt file; am I supposed to make a text file and copy the pasa_config contents to it, and then change those variables?

I'm also slightly confused about how to go about running the PASA program. I wanted to check to make sure things went alright, even if I had nothing configured yet for my mysql db and server and whatnot in that conf.txt file.

---

### Post by drmrgd on 2012-09-25
From the instructions page:

```
After installing each of the software tools above, all that is needed before running PASA is to configure it. The PASA configuration relies on the file: $PASAHOME/pasa_conf/conf.txt

A template configuration file is provided at
$PASAHOME/pasa_conf/pasa.CONFIG.template
Simply copy pasa.CONFIG.template to conf.txt and set the values for your MySQL database settings.  You only need concern yourself with the following values:
PASA_ADMIN_EMAIL=(your email address)
MYSQLSERVER=(your mysql server name)
MYSQL_RO_USER=(mysql read-only username)
MYSQL_RO_PASSWORD=(mysql read-only password)
MYSQL_RW_USER=(mysql all privileges username)
MYSQL_RW_PASSWORD=(mysql all privileges password)
```

Looks like you just copy the template into the appropriate location, and then configure it.  

Then if you continue a little further down the page, it looks like there is a tutorial using sample data.  You might check that out to see how it works.  I don't have time at the moment to mess with MySQL or I'd install it myself to try it out.  Seems fairly straight forward if you have the appropriate input sequence files.  Try out that tutorial with the sample data and see how it goes.

To be honest, this is probably the best and most straightforward guide I've ever seen for a bioinformatics tool.  For comparison, check out the samtools documentation and try to make sense of it!

---

### Post by cdlam on 2012-10-01
Ah sorry! Wasn't able to work on this for a few days. Yeah I had a feeling I was getting in over my head  when I started this. Once I get the stuff running and get into the actual bioinformatics I'll be fine. I'm continually running into this problem though:

> chris@ubuntu:~$ % ../scripts/Launch_PASA_pipeline.pl -c alignAssembly.config -C -R -g genome_sample.fasta \
>  -t all_transcripts.fasta.clean -T -u all_transcripts.fasta -f FL_accs.txt
bash: fg: %: no such job

Using the exact command line from the tutorial. According to the tutorial all those sample files should be in the right place, and the error I'm getting doesn't seem to be related to that. It's probably really simple and I just have no idea what it means lol. I poked around online and didn't really find anything helpful.

---

### Post by drmrgd on 2012-10-02
I think the problem is the '%' in the command you issued.  The authors of that page are indicating the prompt when they list the percent sign (just like you have a dollar sign in your prompt).  I think the % sign is the default prompt of the TCSH shell (you're probably using BASH by default).  So, you can leave that part out when you're running the commands.

Also, I'm not 100% sure on this, but if for some reason the command still fails when you try to run it as you are, add 'perl' to the beginning of that command to explicitly tell BASH to use the Perl interpreter to execute that script.

Hope that helps!

---

### Post by cdlam on 2012-10-02
Well, I got different errors, which is progress I guess lol.
I tried:

> perl ../scripts/Launch_PASA_pipeline.pl -c alignAssembly.config -C -R -g genome_sample.fasta \  -t all_transcripts.fasta.clean -T -u all_transcripts.fasta -f FL_accs.txtand got....

> Can't open perl script "../scripts/Launch_PASA_pipeline.pl": No such file or directory
 It wasn't finding the directory as entered, so I tried it with the full path to the file. So I input:

> chris@ubuntu:~$ perl ~/Documents/PASA/PASA_r2012-06-25/scripts/Launch_PASA_pipeline.pl -c alignAssembly.config -C -R -g genome_sample.fasta  -t all_transcripts.fasta.clean -T -u all_transcripts.fasta -f FL_accs.txtAnd got...
> 
Can't open alignAssembly.config
No such file or directory at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//ConfigFileReader.pm line 12.
Line 12 of the ConfigFileReader is:
> 
sub readConfig {
    my ($filename) = @_;
   [COLOR=Red] open (FILE, $filename) or die "Can't open $filename\n$!";
[/COLOR][COLOR=Red][COLOR=Black]

So is it not finding the ConfigFileReader.pm file, or is it not finding the file specified at line 12 within that file? I rechecked the sample stuff, it's all where it should be...

[/COLOR][/COLOR]

---

### Post by cdlam on 2012-10-02
As a side note, should I make a new thread for this? I'm not sure if it matters for forum rules or anything that we seem to have gone beyond the original purpose of this thread.

Just to see what would happen, I did the option of running the ./run_sample_pipeline.pl as suggested before the beginning of the step-by-step tutorial and got this:

> chris@ubuntu:~/Documents/PASA/PASA_r2012-06-25/sample_data$ perl run_sample_pipeline.pl

Result:

> 
CMD: ../scripts/drop_mysql_db_if_exists.dbi -c alignAssembly.config

Can't locate URI/Escape.pm in @INC (@INC contains: /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib/ /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/../ /home/chris/Documents/PASA/PASA_r2012-06-25/scripts /home/chris/perl5/lib/perl5/x86_64-linux-gnu-thread-multi /home/chris/perl5/lib/perl5 /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Gene_obj.pm line 15.
BEGIN failed--compilation aborted at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Gene_obj.pm line 15.
Compilation failed in require at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Exons_to_geneobj.pm line 8.
BEGIN failed--compilation aborted at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Exons_to_geneobj.pm line 8.
Compilation failed in require at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//CDNA/CDNA_alignment.pm line 25.
BEGIN failed--compilation aborted at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//CDNA/CDNA_alignment.pm line 25.
Compilation failed in require at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Ath1_cdnas.pm line 11.
BEGIN failed--compilation aborted at /home/chris/Documents/PASA/PASA_r2012-06-25/scripts/..//PerlLib//Ath1_cdnas.pm line 11.
Compilation failed in require at ../scripts/drop_mysql_db_if_exists.dbi line 12.
BEGIN failed--compilation aborted at ../scripts/drop_mysql_db_if_exists.dbi line 12.
Error, cmd: ../scripts/drop_mysql_db_if_exists.dbi -c alignAssembly.config died with ret(512)  at run_sample_pipeline.pl line 88. 

---

### Post by drmrgd on 2012-10-02
Well, we have drifted a bit off the original topic.  I don't think it's necessarily a problem, but I'll let an admin come by to tell us otherwise.

Since I haven't fully compiled and installed this package, it's going to be a bit hard to troubleshoot.  Overall, it looks like the script is looking for things that you either don't have or are in a different place than the script predicts they will be.  The way the first string reads to me, it's saying (basically) "from the directory you're running the script, go up one level and into the "scripts" folder, and execute the script "Launch_PASA_pipeline.pl", use the "alignAssembly.config" in that same folder using the rest of the files in the command string execute the script.  I'm not sure what all the options do and are for (you might check the docs for that).  So, my first guess is that you're either executing the script in such a way as to not be able to find the "Launch...." script the first time, and then not to be able to find something different the second time.  The Perl variable '@_' indicates the parameters that were sent to a function as stored in an array (I'm not a Perl wizard by any means, but that should essentially be everything else after the .pl file!).  I'm guessing it's looking for the alignAssembly.config file, but I might be misinterpreting the error.  Can you confirm that you do have that config file, it's been properly set up, and that it's in the location listed by the error?

The second block of errors is due to the script looking for a bunch of libraries (more properly Perl Modules, hence the .pm), which either do not exist or are not in your Perl Module Path (@INC).  Without digging through the scripts and docs, it's hard to say what's missing here.  I would confirm, at least as a first step, that you do have those Perl modules installed and that the location of them is in your @INC path.  Again, being a complete Perl novice, I'm not sure exactly how to modify this variable to point to the correct location(s).  So, I think I'm not going to be tons of help here. Overall, I would just double check that you have everything, that everything is installed where it should be, and that you're calling the scripts from the appropriate locations.   

At this point, as it's very specific to the program and I just don't have time at the moment to install and test it, you might consider sending some of these errors to the developers or people at their listserv.  They might be able to help you a little more quickly than I can guess at it.  Also, since no one has chimed in here all this time, I'm guessing that no one else on this forum has played with the software either.  I'm happy to still help where I can, though!

---

