---
title: "C++ blocking at EOF"
date: 2010-02-17
forum: Programming Talk
---

### Post by tbastian on 2010-02-17
I'm writing an application that reads from a file while another program is writing to it. I'd like it to block when it reaches the EOF so that I can wait on more data. Is there any nice way of doing that without polling?

---

### Post by tbastian on 2010-02-17
right now I'm just using this:

```

// blocks until data is available
void ReadBuffer::block ()
{
	while ( file.eof () ) {
		usleep ( 25000 );
	}
}

```

---

### Post by gvoima on 2010-02-17
Are you closing the while between writes, or is it always open?

---

### Post by dwhitney67 on 2010-02-17
I've done something similar to what you need, and the way I did it was merely one of perhaps half-a-dozen ways one could solve the issue.

In my case, my local app needed to read all of the data out of a file, and send it via a socket, to remote server.  If the local app lost communications with the remote server, then it would exit it's 'read' mode, and begin it's 'write' mode where new data would be appended to the file.

Once comm was re-established with the remote server, the local app returned to it's 'read' mode and began sending data again from the *exact* point where it left off before.  Thus any data stored during the period where there was a loss of comm, was read and sent until an EOF was once again encountered.

Anyhow, the way I did this was to merely keep a place-marker of where the file-pointer was in the file, so that if I had to re-open the file for reading, I could immediately jump to that spot to begin reading.

In your case, your reader app could read the entire file, and keep a marker where the last successful read occurred.  Then close the file.  Periodically, re-open the file, jump to the point where you left off, and attempt to read some more data.  Repeat this as needed, indefinitely.

As I stated earlier, this is just one solution.  Another solution could be to use popen() with the command 'tail -f somefile'.  From there, just read the results as furnished through the pipe.  This will probably be your best bet if both applications are running under the same system.

---

### Post by tbastian on 2010-02-17
> **dwhitney67 said:**
> I've done something similar to what you need, and the way I did it was merely one of perhaps half-a-dozen ways one could solve the issue.

In my case, my local app needed to read all of the data out of a file, and send it via a socket, to remote server.  If the local app lost communications with the remote server, then it would exit it's 'read' mode, and begin it's 'write' mode where new data would be appended to the file.

Once comm was re-established with the remote server, the local app returned to it's 'read' mode and began sending data again from the *exact* point where it left off before.  Thus any data stored during the period where there was a loss of comm, was read and sent until an EOF was once again encountered.

Anyhow, the way I did this was to merely keep a place-marker of where the file-pointer was in the file, so that if I had to re-open the file for reading, I could immediately jump to that spot to begin reading.

In your case, your reader app could read the entire file, and keep a marker where the last successful read occurred.  Then close the file.  Periodically, re-open the file, jump to the point where you left off, and attempt to read some more data.  Repeat this as needed, indefinitely.

As I stated earlier, this is just one solution.  Another solution could be to use popen() with the command 'tail -f somefile'.  From there, just read the results as furnished through the pipe.  This will probably be your best bet if both applications are running under the same system.

I've got the polling working, and I think it may turn out to be good enough for what I'm doing. The file should be updated very frequently, so I don't think that opening and closing the file would be the answer, but I'm interested in checking out the 'popen()' solution, however I can't find any good descriptions about what it does and how it does it... can you recommend anything?

---

