---
title: "NR_FILE NR_OPEN temporary increase"
date: 2008-03-12
forum: Programming Talk
---

### Post by Daem0hn on 2008-03-12
Hello All,

I'm hoping that this is the right forum to post this question in, if not, I appologise.

The question:
Would increasing NR_FILE and NR_OPEN to 500,000+ (up from 8192,1024 respectively) cause issues if the file handles were fully utilised?

Is there a quick, once-off way of increasing them (similar to echo xxxxxxx > /proc/sys/kernel/shmmax temporarily increases SHMMAX, or altering kern.maxfiles in /boot/loader.conf in BSD)? or do they require a kernel recompile? (all the googling i have done indicates the latter).


I've never run into this problem before, file handle limits imposed on processes (and the system in general) are too small. I only require a one time increase (however the increase is quite significant).

The problem occurs because i have 480,000 files requiring 350,000,000+ lines of randomly organised data (100 chars per line) to be appended to the files. Each line of data contains a flag indicating to which file it should be appended.

Fairly simple code, yes.

read line, decide which file to append the data to, open the file to append, append, close the file, move onto the next line.

Now this works. I have a program which does just that. The issue is the speed of access.

As more lines of data are appended to the files, the files become longer (obviously) and hence the 'open for append' operation takes longer to seek to the end of the file and become ready for append. After running this program for a day, and calculating based on the rate at which it was slowing down, that it would take 8.5 days to complete, i decided to seek another solution.

The easiest solution I thought of (without considering the implications of open file limits), was to create an array of 480,000 fstreams, each one remaining open for an append. This would mean no seeking after the initial open.

Obviously I considered holding the data in RAM and dumping, however there is too much data to fit into RAM (i have 4 gigs, the minimum size the data would take is 6 gigs)



The question i have, is that the default Ubuntu kernel comes with a per process limit #define NR_OPEN 1024 (as per limits.h) and a system wide limit of #define NR_FILE 8192 (as per fs.h)

In my time using linux, i've done plenty of kernel recompiles (my first linux experience was gentoo '03 stage 1 install, boy that was a steep learning curve), but i've never played around with NR_FILE and NR_OPEN. From your experience (if anyone has any), would increasing these values to say, 500,000 cause problems, assuming the 500,000 per process limit is fully utilized?

Also, is there a faster way of temporarily altering these values (like echoing to /proc/sys/kernel/shmmax to change shared memory? or editing /boot/loader.conf in BSD) or do they require a kernel recompile (all the google results i have found indicate the latter). The only reason i ask, is that this processing only needs to happen once.


Thanks in advance for your help.
If anyone has any other suggestions as to how I can (in a timely fashion) process the data, please let me know.


Cheers,
Mike

---

### Post by Daem0hn on 2008-03-13
I decided that i'd take a bit of a performance hit (w.r.t. the array of fstreams) and create a write buffer for each file, only opening the files when the buffer was full. That worked - although took a little longer than it would have otherwise.

Still no solution regarding the NR_FILE and NR_OPEN situation. If anyone knows, I would be interested in knowing the answer.

Cheers,
Mike

---

### Post by NathanB on 2008-03-14
> **Daem0hn said:**
> I decided that i'd take a bit of a performance hit (w.r.t. the array of fstreams) and create a write buffer for each file, only opening the files when the buffer was full. That worked - although took a little longer than it would have otherwise.

It is good to see that you are thinking more data-centric rather than file-centric in solving this issue.  Another option you could try is to do all of your processing within the confines of a database.  After all of the processing is finished, then you can generate all the files that you need.

Take a look at SQLite:   [http://www.sqlite.org/](http://www.sqlite.org/)

The following quote from the Appropriate Uses page ( [http://www.sqlite.org/whentouse.html](http://www.sqlite.org/whentouse.html) ) seems to fit your situation.
> Internal or temporary databases

For programs that have a lot of data that must be sifted and sorted in diverse ways, it is often easier and quicker to load the data into an in-memory SQLite database and use queries with joins and ORDER BY clauses to extract the data in the form and order needed rather than to try to code the same operations manually. Using an SQL database internally in this way also gives the program greater flexibility since new columns and indices can be added without having to recode every query.


Nathan.

---

### Post by nanotube on 2008-03-14
> **NathanB said:**
> It is good to see that you are thinking more data-centric rather than file-centric in solving this issue.  Another option you could try is to do all of your processing within the confines of a database.  After all of the processing is finished, then you can generate all the files that you need.

Take a look at SQLite:   [http://www.sqlite.org/](http://www.sqlite.org/)

The following quote from the Appropriate Uses page ( [http://www.sqlite.org/whentouse.html](http://www.sqlite.org/whentouse.html) ) seems to fit your situation.


Nathan.

yea, but he just said that he cant fit all the data in memory... so it'll have to be an on-disk sqlite db. though, being a db, it's seek operations may be more efficient than a flatfile, so even an on-disk db may work fast enough. (i don't have enough experience with sqlite to know offhand whether that would be true, though...)

---

### Post by Daem0hn on 2008-03-14
SQLLite, I never even considered it but will have a look, hopefully it has some fast and nifty ways of storing huge amounts of data on disk.

I wrote databases off after some annoyances with MySQL/c++ API and slowness of postgres/mysql in general. It seems that running select/avg/sum/join/stddev queries on 350,000,000 tuples is larger scale than what most databases can handle within the realms of my attention span :P

currently i've divided the problem into a few steps.

As the data is static, all processing of the data only needs to occur once.

Step 1 is pre-processing the data from the 350,000,000 lines of data, into the 480,000 files for easier processing. Much like a select query, grouping by file i suppose.

Step 2 is to process the preprocessed data. This involves processing the 480,000 files into large structs that contain the mathematical relationships and values that i am interested in.
These structs can then be serialized.

Step 3 is to use the structs and the contained mathematical relationships to perform dynamic calculations and estimations.


So essentially I am spending a while preprocessing the data into the final calculated forms which can then be used in estimations and approximations.

Currently my C++ program is churning away (significantly faster than the database method).

Thanks for your suggestions guys, I'll definitely look into it, see if it would be a worthwhile contender for providing dynamic access to the final processed data.

Cheers.
Mike

---

