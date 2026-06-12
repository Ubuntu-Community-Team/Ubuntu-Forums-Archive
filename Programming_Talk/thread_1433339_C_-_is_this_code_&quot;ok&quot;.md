---
title: "C - is this code &quot;ok&quot;?"
date: 2010-03-18
forum: Programming Talk
---

### Post by ApEkV2 on 2010-03-18
Just want to make sure this code is 100% ok, and also are there any ways to make this program faster?

I was trying to use pthread, but ran into numerous problems, the biggest being it trying to rmdir before a thread has finished working.
(results in a "folder not empty") also this program can delete files owned by root if used with sudo, so don't do so.

I'm surprised how fast this program runs actually, 15000 files (@ 400mb) in under 2.2 seconds.
Used (double)(end - start)/CLOCKS_PER_SEC; to come up with the time, so I don't know if that's accurate.

So are there any problems with my syntax (a good mixture of k&r and allman?), and are there any ways to make this faster?
Also is it easy to read and has good etiquette? Tried to keep comments at a bare minimum (they clutter things up) 
Maybe some good links to tutorials for pthread/mutex? Is it even conceivable to make this multi-threaded?

```
/*//////////////////////////////////////////////////*/
// WARNING: DO NOT USE THIS PROGRAM AS ROOT [ie sudo]
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*//////////////////////////////////////////////////*/
/* Created by ApEk / Usage: [command] [path] [path] */

struct stat buf;
struct dirent *dep;
void Toptier(char *);
void KO_file(char *,int);

int main(int argc, char *argv[])
{
	int x = 1;
	for (; argv[x] != NULL; ++x)
	{
		stat(argv[x], &buf);
		if (S_ISDIR(buf.st_mode)) {
			Toptier(argv[x]);
		}
		else if (S_ISREG(buf.st_mode)) {
			KO_file(argv[x],0);
		}
		else if (S_ISLNK(buf.st_mode)) {
			unlink (argv[x]);
		}
		
	}
	return 0;
}

/*//////////////////////////////////////////////////*/
// This function handles the main recursion,

void Toptier(char *argv)
{
	DIR *dirp = opendir(argv);
	if (dirp == NULL)  return;

	while ((dep = readdir(dirp)) != NULL)
	{
		if (!strcmp(".",dep->d_name) || !strcmp("..",dep->d_name))
			continue;
			
		char *path = malloc(strlen(argv) + strlen(dep->d_name)+2);
		sprintf(path, "%s/%s", argv, dep->d_name);
		
		if (dep->d_type == DT_DIR) {
			Toptier(path);
		}
		else if (dep->d_type == DT_REG) {
			KO_file(path,1);
		}
		else if (dep->d_type == DT_LNK) {
			unlink (path);
		}

		free(path);
	}
	closedir(dirp);
	rmdir(argv);
}

/*//////////////////////////////////////////////////*/
// This function writes to, and deletes the target

void KO_file(char *path, int ifon)
{
	FILE* fdes = fopen(path,"r+");
	if (fdes == NULL) return; // -1 EACCES
	
	ifon > 0 ? stat(path, &buf) : ifon;
	char *buffer = malloc(buf.st_size);
	buffer = memset(buffer, 0x01, buf.st_size);
	fputs(buffer, fdes);

	free(buffer);
	fclose(fdes);
	unlink(path);
}

/*//////////////////////////////////////////////////*/
// DISCLAIMER: This program deletes files and folders
```
Also thx Dwhitney for helping with the recursion, by far the simplest solution.
EDIT: also, I recovered shredded files with ntfsundelete, and from a hex editor they are shredded (filled with 0x01's)

---

### Post by soltanis on 2010-03-19
Well if you recovered it and found it overwritten then no problem there.

Although from what I hear about ext3+ and other journaled file systems, even though you may have overwritten the file, you may not have overwritten the file on the disk...though, if you have recovered and examined it, you probably did that ok.

---

### Post by MadCow108 on 2010-03-19
allocating a memory of the size of the file in KO_file may be a problem.
What if the file is larger than the available ram?
consider just overwriting it directly (e.g. fputc)

> **ApEkV2 said:**
> Is it even conceivable to make this multi-threaded?

you can make it multithreaded but you won't gain performance when working with a single harddisk. So when you don't plan to make your program interactive it does not make much sense.

I also suspect you have not really shredded the file, 2.2 seconds for 400 mb seem a bit fast (hd generic write speed is usually around 30mb/s).
Shredding files properly on journaled filesystems is quite difficult I've heard.
You have to write a special implementation for every filesystem you want to use it on.

---

### Post by ApEkV2 on 2010-03-19
@ MadCow and soltanis, I only tested to see if it was shredded on an ntfs filesystem, and it worked.
About the memory allocation, I originally used fputc, but that took more than twice as long, and used alot more cpu time.
I should probably have it test for large files and then break it up as necessary. Shouldn't be hard.

And about whether it is actually working on ext4, I don't know if it is or not. I need a program to recover files from ext4.
It seems nonphysically possible that 15000 files completed in 2 seconds, as it takes an average 3-10ms to find the file on the disk.

---

### Post by pbrane on 2010-03-19
Wouldn't it be easier to test if you don't delete the shredded files. Check them, and if they are completely overwritten then you can add the deletion code back in. Also as I understand it, most algorithms for secure deletion overwrite the files multiple times.

---

### Post by ApEkV2 on 2010-03-19
I already tried uncommenting the unlink and rmdir, and they are overwritten with 0x01's.
That's not the problem, I might've hit a bottleneck with the harddrive, and some files might not have been successful.

About deleting them multiple times, they only do that to eliminate the "shadow" of itself on the drive.
You wouldn't have to do this on ssd's.

---

### Post by MadCow108 on 2010-03-19
just because the file is overwritten when you look at it that does not mean there is no copy of the original left somewhere.
Especially on journaled filesystems

even the unix program shred does not claim to work on journaled systems
> 
The following are examples of file systems on which shred is not
effective, or is not guaranteed to be effective in all file system modes:

       * log-structured or journaled file systems, such as those supplied with

              AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       * file systems that write redundant data and carry on even if some writes

              fail, such as RAID-based file systems

       * file systems that make snapshots, such as Network Appliance&#8217;s NFS server

       * file systems that cache in temporary locations, such as NFS

              version 3 clients

       * compressed file systems


btw very excessive shredding on ssd's may be a bad idea as it reduces the ssd's lifetime (depending on quality and if a wear level algorithm is used)

---

### Post by gmargo on 2010-03-19
> 
Just want to make sure this code is 100% ok, and also are there any ways to make this program faster?
Since you're asking for a critique:
There are several holes in this program that should be
addressed before wasting your time on speed.
And I won't even address the folly of overwriting file content.
(BTW, have you seen the **shred** package?)

1. Recursion is a problem as implemented.
Since you have a limited number of file descriptors, it is dangerous
to recurse while leaving the parent directory file descriptors open.

2. Error checking.  You simply ignore errors (opendir, fopen)
or don't check (star, unlink, malloc, rmdir) instead of printing
an appropriate error message.  Some errors are fatal, others aren't.

3. Global variables.  "buf" and "*dep" should not be global!
While the code doesn't appear to have a problem with this at the
moment, any simple code change could cause mysterious errors.
And it costs nothing to use local variables instead.

4. What does this statement do?
You couldn't come up with a better way to code that?
```

   ifon > 0 ? stat(path, &buf) : ifon;

```Plus it's pointless to bother avoiding a single stat.
And it requires that silly global.

---

### Post by dwhitney67 on 2010-03-19
> **gmargo said:**
> 
1. Recursion is a problem as implemented.
Since you have a limited number of file descriptors, it is dangerous
to recurse while leaving the parent directory file descriptors open.


Do you really think this is an issue?  How many files do you think will be opened?

I did a little research, and found that on my puny home notebook computer, I could potentially have open up over 200,000 files/sockets at once.
```

cat /proc/sys/fs/file-max
203047

```
At work, on a CentOS system, over 382,000 files/sockets.

Considering that most files on a system are regular files, and not directories, reaching that limit might prove to be difficult.

With the OP's program, after a regular file has been processed, it is closed, thus freeing a file descriptor that can be utilized again.

---

### Post by ApEkV2 on 2010-03-19
> **gmargo said:**
> 2. Error checking.  You simply ignore errors (opendir, fopen)
or don't check (star, unlink, malloc, rmdir) instead of printing
an appropriate error message.  Some errors are fatal, others aren't.

3. Global variables.  "buf" and "*dep" should not be global!
While the code doesn't appear to have a problem with this at the
moment, any simple code change could cause mysterious errors.
And it costs nothing to use local variables instead.

@ 2, errors like EACCES? that's what the returns are for. ENOTEMPTY from rmdir doesn't need to be dealt with, because if it fails, I can't do anything about it.
I'm using this code with nautilus-actions, so I don't need to print error messages.

@ 3, they are global because this code is single threaded. If it was other, I wouldn't have put them as global.

---

### Post by Compyx on 2010-03-19
> **dwhitney67 said:**
> Do you really think this is an issue?  How many files do you think will be opened?

I did a little research, and found that on my puny home notebook computer, I could potentially have open up over 200,000 files/sockets at once.
```

cat /proc/sys/fs/file-max
203047

```
At work, on a CentOS system, over 382,000 files/sockets.

Considering that most files on a system are regular files, and not directories, reaching that limit might prove to be difficult.

With the OP's program, after a regular file has been processed, it is closed, thus freeing a file descriptor that can be utilized again.

Actually that's what the kernel allows, to check what the C library supports you should examine the macro FOPEN_MAX, which on my system reports 16 (that includes stdin, stdout and stderr, leaving 13 file descriptors for the user). But that's just if want maximum portability; using POSIX' `sysconf(_SC_OPEN_MAX)' I get 1024.

---

### Post by Compyx on 2010-03-19
OK, did a little research using this little gem:
[php]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

/* some arbitrary number */
#define FD_MAX  4096

int main(void)
{
    FILE *fp[FD_MAX];
    int fd;

    /* let's see how far we get */
    for (fd = 0; fd < FD_MAX; fd++) {
        printf("opening file #%d ... ", fd + 1);
        fflush(stdout);
        /* open temporary file */
        fp[fd] = tmpfile();
        /* check for errors */
        if (fp[fd] == NULL) {
            /* aha! hit the jackpot */
            fprintf(stderr, "error (%d): %s\n", errno, strerror(errno));
            return EXIT_FAILURE;
        }
        puts("OK");
    }
    /* make limit bigger next time ;) */
    printf("Holy crap, managed to open %d files at once!\n", FD_MAX);
    puts("Increase limit and recompile.");
    return EXIT_SUCCESS;
}
[/php]

Output (last few lines):
```

opening file #1019 ... OK
opening file #1020 ... OK
opening file #1021 ... OK
opening file #1022 ... error (24): Too many open files
compyx@aspire7730g:~$ 

```

And 1021 just happens to be 1024 - (stdin, stdout, stderr). So, at least on my system, the per-process limit indeed seems to be 1024, using the standard C library.
Quite a bit more than FOPEN_MAX's 16 ;)

---

### Post by ApEkV2 on 2010-03-20
I doubt having 1021 open parent directories will ever happen in normal situations.
But I tried solving the memory problem, now the max size for the buffer is 2mb. Since most files are smaller.
Someone won't like the fact I used more globals.
```
/*//////////////////////////////////////////////////*/
// WARNING: DO NOT USE THIS PROGRAM AS ROOT [ie sudo]
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*//////////////////////////////////////////////////*/
/* Created by ApEk / Usage: [command] [path] [path] */

struct stat buf;
struct dirent *dep;
unsigned temp, inc;
void Toptier(char *);
void KO_file(char *);
#define _2MEG 2097152

int main(int argc, char *argv[])
{
	int x = 1;
	for (; argv[x] != NULL; ++x)
	{
		stat(argv[x], &buf);
		if (S_ISDIR(buf.st_mode)) {
			Toptier(argv[x]);
		}
		else if (S_ISREG(buf.st_mode)) {
			KO_file(argv[x]);
		}
		else if (S_ISLNK(buf.st_mode)) {
			unlink (argv[x]);
		}
		
	}
	return 0;
}

/*//////////////////////////////////////////////////*/
// This function handles the main recursion,

void Toptier(char *argv)
{
	DIR *dirp = opendir(argv);
	if (dirp == NULL)  return;

	while ((dep = readdir(dirp)) != NULL)
	{
		if (!strcmp(".",dep->d_name) || !strcmp("..",dep->d_name))
			continue;
			
		char *path = malloc(strlen(argv) + strlen(dep->d_name)+2);
		sprintf(path, "%s/%s", argv, dep->d_name);
		
		if (dep->d_type == DT_DIR) {
			Toptier(path);
		}
		else if (dep->d_type == DT_REG) {
			KO_file(path);
		}
		else if (dep->d_type == DT_LNK) {
			unlink (path);
		}

		free(path);
	}
	closedir(dirp);
	rmdir(argv);
}

/*//////////////////////////////////////////////////*/
// This function writes to, and deletes the target

void KO_file(char *path)
{
	FILE* fdes = fopen(path,"r+");
	if (fdes == NULL) return; // -1 EACCES
	stat(path, &buf);
	temp = buf.st_size;
	
	_2MEG < temp ? temp = _2MEG : temp;
	char *buffer = malloc(temp);
	buffer = memset(buffer,0x01, temp);
	
	for (inc = 0; inc < buf.st_size;) {
		if (inc+temp <= buf.st_size) {
			fputs(buffer, fdes);
			inc += temp;
		} else {
			fputc(0x01, fdes);
			++inc;
		}
	} // If you don't have 2MB available
	  // shame on you, I mean come on !!
		
	free(buffer);
	fclose(fdes);
	unlink(path);
}

/*//////////////////////////////////////////////////*/
// DISCLAIMER: This program deletes files and folders
```

EDIT: say if I want to delete the contents of a mounted harddrive, could I use another wrapper program that creates individual threads of the above code?
(ie) using execv/pthread or similar in the wrapper program? I know that harddrives wouldn't allow such speed, but when ssd's become the norm,

---

