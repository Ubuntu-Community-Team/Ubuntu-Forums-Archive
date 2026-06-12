---
title: "Installed programs not running in Amazon EC2 instance. (Newbie question.)"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Syriloth on 2012-09-27
OK, this is a total newbie question so please bear with me. I have tried to find a solution but I probably am just too ignorant to know what search terms I ought to be using to find the answers I need. If the solution to my problem is already documented elsewhere, or if there is a more appropriate forum for this question, please feel free to direct me to that.

I'm a biology student and I've been tasked by my principal investigator (PI) with investigating the possibility of using EC2 as a source of on-demand computing power for conducting phylogenetic analyses. We have a few tools that we need to be able to run, including [STRUCTURE]("http://pritch.bsd.uchicago.edu/software/structure2_1.html") and [IMa2]("http://cbsuapps.tc.cornell.edu/IMa2.aspx"). Both of these come with linux console editions, and I am currently trying to get them running on a Micro instance running Ubuntu 12.04 Server.

I am having no trouble accessing the instance via SSH, uploading files to it via SCP, navigating the filesystem, or installing and running official packages via apt-get. However the tools that I need to run don't seem to be working at all. I feel like there must be something incredibly obvious that I am missing.

For instance, when attempting to install an run STRUCTURE, I follow the instructions given on the developer's website for console Linux users: 'The downloaded files are compressed in zip files; uncompress them using "unzip filename" on Unix/Linux/Mac OS X system or using winzip on windows. The zip files contain an executable and parameter files, as well as a sample data file "testdata1". The program is set up to run on these data immediately (just type "./structure" to start the program).'

I can get the package up onto the instance and I have unzipped it into /home/ubuntu/structure/console . There I find a total of six files: extraparams, mainparams, structure, structure_doc.pdf, and testdata1. So far everything looks like it should as far as my naive eyes can discern. When I enter "./structure" from within /home/ubuntu/structure/console, I simply get the reply "-bash: ./structure: No such file or directory".

I get similar errors when I attempt to install and run IMa2. I am stymied by this. I'm sure that if I knew the first thing about Linux or EC2 then the solution would be obvious, but I think the solution is probably so obvious that I can't even find where I ought to be looking. If someone could straighten me out then I would greatly appreciate it. I will check back on this thread to provide whatever clarifying information might be required by whatever generous and long-suffering souls are willing to assist me, as I'm sure that in my ignorance I've neglected to provide all kinds of important information.  

Many thanks in advance.

---

### Post by drmrgd on 2012-09-27
My guess is that the two files you're trying to run are currently not set as executable.  As a test, go into the Structure folder (for example), and type:

```
ls -l
```

Please put the output here using the code tags (the hash marks). 

What you want to see is something like:

```
-rwxr-xr-x
```

As the first string of the file.  The "x", one of the types of permissions on a linux file, indicates whether or not the file is executable.  If you don't see any x's, that means that it needs to be changed.  You can do that by typing:

```
chmod +x structure
```

Then check that you have the correct permissions set on the file so that typing ./structure will work.

---

### Post by Syriloth on 2012-09-27
Crap, I fixed it. I knew I had execute permissions but it still wasn't working. Then I remembered that I had read somewhere that I would need 32-bit compatibility libraries to run 32-bit software under Unbuntu Server. I'd tried installing ia32-libs via apt-get but it had failed. I tried again using aptitude and it worked, and now I can run Structure! So I've cleared that hurdle.

Thanks for the advice though, I feel a bit silly now. Glad it's fixed though.

---

