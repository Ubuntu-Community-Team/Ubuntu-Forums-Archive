---
title: "Profiling MPI apps"
date: 2006-09-11
forum: Programming Talk
---

### Post by yourself on 2006-09-11
Hello

I've been frantically trying to analyze the performance of my MPI app. I have the .clog file but everything that could actually be used to display results (upshot, jumpshot, ...) is missing. (Missing, or being there as dead links: for example /usr/bin/upshot points to non-existent /etc/alternatives/upshot)

The only thing that could actually do something was clog_print, which is of course hardly useful.

I've tried searching for jumpshot using apt-file, no results.

Of course the one manual page I found (usr/lib/mpich/man/man1/Jumpshots.1.gz, part of package mpich-bin) was referring to a certain logviewer which is a wrapper script that launches the 'correct' jumpshot for each logfile type, and of course: /usr/bin/logviewer points to non-existent /etc/alternatives/logviewer....

Is there any way I could analyze my .clog file?
(One way would be reinstalling the entire mpi from source, but I believe that's exactly why we have apt, so is there anything other than reinstalling?)

Thanks

---

### Post by alkalined on 2007-05-19
Seems like there are not many people into parallel programming here.
I've been struggling with this too just to find only a bunch of dead links in the mpich directories.
Just wanted to revive the thread. Any suggestions are welcome :)

---

### Post by Kallikanzarid on 2010-06-13
Scalasca should be good, but I haven't checked it out yet.

---

### Post by soltanis on 2010-06-13
Hooray resurrecting dead threads.

---

