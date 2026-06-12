---
title: "How can I print current folder name like &quot;pwd&quot; ?(Module Programming"
date: 2009-12-12
forum: Programming Talk
---

### Post by fenerista on 2009-12-12
I want to make a module that print console, current folder name like pwd, but I don't know how.  With system calls ? or something else ? if system calls, what is the system call of that ? and how can I use this system call on my module?

Programming Language : C

---

### Post by era86 on 2009-12-12
> **fenerista said:**
> I want to make a module that print console, current folder name like pwd, but I don't know how.  With system calls ? or something else ? if system calls, what is the system call of that ? and how can I use this system call on my module?

Pardon my ignorance, but what language will this be in?

---

### Post by grayrainbow on 2009-12-12
man getcwd

---

### Post by fenerista on 2009-12-12
> **era86 said:**
> pardon my ignorance, but what language will this be in?

sorry,

language is "C"

---

### Post by fenerista on 2009-12-12
> **grayrainbow said:**
> man getcwd

is it possible to use getchwd in module(kernel space) 
I saw getcwd is being used in user space programs(int main(){...) normal C programs but I don't know how it is using in modules or can it ?

---

### Post by fenerista on 2009-12-12
And pwd.c from coreutils 8.1

```
/* pwd - print current directory
   Copyright (C) 1994-1997, 1999-2009 Free Software Foundation, Inc.

   This program is free software: you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation, either version 3 of the License, or
   (at your option) any later version.

   This program is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.

   You should have received a copy of the GNU General Public License
   along with this program.  If not, see <http://www.gnu.org/licenses/>.  */

#include <config.h>
#include <getopt.h>
#include <stdio.h>
#include <sys/types.h>

#include "system.h"
#include "error.h"
#include "quote.h"
#include "root-dev-ino.h"
#include "xgetcwd.h"

/* The official name of this program (e.g., no `g' prefix).  */
#define PROGRAM_NAME "pwd"

#define AUTHORS proper_name ("Jim Meyering")

struct file_name
{
  char *buf;
  size_t n_alloc;
  char *start;
};

static struct option const longopts[] =
{
  {"logical", no_argument, NULL, 'L'},
  {"physical", no_argument, NULL, 'P'},
  {GETOPT_HELP_OPTION_DECL},
  {GETOPT_VERSION_OPTION_DECL},
  {NULL, 0, NULL, 0}
};

void
usage (int status)
{
  if (status != EXIT_SUCCESS)
    fprintf (stderr, _("Try `%s --help' for more information.\n"),
             program_name);
  else
    {
      printf (_("Usage: %s [OPTION]...\n"), program_name);
      fputs (_("\
Print the full filename of the current working directory.\n\
\n\
"), stdout);
      fputs (_("\
  -L, --logical   use PWD from environment, even if it contains symlinks\n\
  -P, --physical  avoid all symlinks\n\
"), stdout);
      fputs (HELP_OPTION_DESCRIPTION, stdout);
      fputs (VERSION_OPTION_DESCRIPTION, stdout);
      printf (USAGE_BUILTIN_WARNING, PROGRAM_NAME);
      emit_ancillary_info ();
    }
  exit (status);
}

static void
file_name_free (struct file_name *p)
{
  free (p->buf);
  free (p);
}

static struct file_name *
file_name_init (void)
{
  struct file_name *p = xmalloc (sizeof *p);

  /* Start with a buffer larger than PATH_MAX, but beware of systems
     on which PATH_MAX is very large -- e.g., INT_MAX.  */
  p->n_alloc = MIN (2 * PATH_MAX, 32 * 1024);

  p->buf = xmalloc (p->n_alloc);
  p->start = p->buf + (p->n_alloc - 1);
  p->start[0] = '\0';
  return p;
}

/* Prepend the name S of length S_LEN, to the growing file_name, P.  */
static void
file_name_prepend (struct file_name *p, char const *s, size_t s_len)
{
  size_t n_free = p->start - p->buf;
  if (n_free < 1 + s_len)
    {
      size_t half = p->n_alloc + 1 + s_len;
      /* Use xnmalloc+free rather than xnrealloc, since with the latter
         we'd end up copying the data twice: once via realloc, then again
         to align it with the end of the new buffer.  With xnmalloc, we
         copy it only once.  */
      char *q = xnmalloc (2, half);
      size_t n_used = p->n_alloc - n_free;
      p->start = q + 2 * half - n_used;
      memcpy (p->start, p->buf + n_free, n_used);
      free (p->buf);
      p->buf = q;
      p->n_alloc = 2 * half;
    }

  p->start -= 1 + s_len;
  p->start[0] = '/';
  memcpy (p->start + 1, s, s_len);
}

/* Return a string (malloc'd) consisting of N `/'-separated ".." components.  */
static char *
nth_parent (size_t n)
{
  char *buf = xnmalloc (3, n);
  char *p = buf;
  size_t i;

  for (i = 0; i < n; i++)
    {
      memcpy (p, "../", 3);
      p += 3;
    }
  p[-1] = '\0';
  return buf;
}

/* Determine the basename of the current directory, where DOT_SB is the
   result of lstat'ing "." and prepend that to the file name in *FILE_NAME.
   Find the directory entry in `..' that matches the dev/i-node of DOT_SB.
   Upon success, update *DOT_SB with stat information of `..', chdir to `..',
   and prepend "/basename" to FILE_NAME.
   Otherwise, exit with a diagnostic.
   PARENT_HEIGHT is the number of levels `..' is above the starting directory.
   The first time this function is called (from the initial directory),
   PARENT_HEIGHT is 1.  This is solely for diagnostics.
   Exit nonzero upon error.  */

static void
find_dir_entry (struct stat *dot_sb, struct file_name *file_name,
                size_t parent_height)
{
  DIR *dirp;
  int fd;
  struct stat parent_sb;
  bool use_lstat;
  bool found;

  dirp = opendir ("..");
  if (dirp == NULL)
    error (EXIT_FAILURE, errno, _("cannot open directory %s"),
           quote (nth_parent (parent_height)));

  fd = dirfd (dirp);
  if ((0 <= fd ? fchdir (fd) : chdir ("..")) < 0)
    error (EXIT_FAILURE, errno, _("failed to chdir to %s"),
           quote (nth_parent (parent_height)));

  if ((0 <= fd ? fstat (fd, &parent_sb) : stat (".", &parent_sb)) < 0)
    error (EXIT_FAILURE, errno, _("failed to stat %s"),
           quote (nth_parent (parent_height)));

  /* If parent and child directory are on different devices, then we
     can't rely on d_ino for useful i-node numbers; use lstat instead.  */
  use_lstat = (parent_sb.st_dev != dot_sb->st_dev);

  found = false;
  while (1)
    {
      struct dirent const *dp;
      struct stat ent_sb;
      ino_t ino;

      errno = 0;
      if ((dp = readdir_ignoring_dot_and_dotdot (dirp)) == NULL)
        {
          if (errno)
            {
              /* Save/restore errno across closedir call.  */
              int e = errno;
              closedir (dirp);
              errno = e;

              /* Arrange to give a diagnostic after exiting this loop.  */
              dirp = NULL;
            }
          break;
        }

      ino = D_INO (dp);

      if (ino == NOT_AN_INODE_NUMBER || use_lstat)
        {
          if (lstat (dp->d_name, &ent_sb) < 0)
            {
              /* Skip any entry we can't stat.  */
              continue;
            }
          ino = ent_sb.st_ino;
        }

      if (ino != dot_sb->st_ino)
        continue;

      /* If we're not crossing a device boundary, then a simple i-node
         match is enough.  */
      if ( ! use_lstat || ent_sb.st_dev == dot_sb->st_dev)
        {
          file_name_prepend (file_name, dp->d_name, _D_EXACT_NAMLEN (dp));
          found = true;
          break;
        }
    }

  if (dirp == NULL || closedir (dirp) != 0)
    {
      /* Note that this diagnostic serves for both readdir
         and closedir failures.  */
      error (EXIT_FAILURE, errno, _("reading directory %s"),
             quote (nth_parent (parent_height)));
    }

  if ( ! found)
    error (EXIT_FAILURE, 0,
           _("couldn't find directory entry in %s with matching i-node"),
             quote (nth_parent (parent_height)));

  *dot_sb = parent_sb;
}

/* Construct the full, absolute name of the current working
   directory and store it in *FILE_NAME.
   The getcwd function performs nearly the same task, but is typically
   unable to handle names longer than PATH_MAX.  This function has
   no such limitation.  However, this function *can* fail due to
   permission problems or a lack of memory, while GNU/Linux's getcwd
   function works regardless of restricted permissions on parent
   directories.  Upon failure, give a diagnostic and exit nonzero.

   Note: although this function is similar to getcwd, it has a fundamental
   difference in that it gives a diagnostic and exits upon failure.
   I would have liked a function that did not exit, and that could be
   used as a getcwd replacement.  Unfortunately, considering all of
   the information the caller would require in order to produce good
   diagnostics, it doesn't seem worth the added complexity.
   In any case, any getcwd replacement must *not* exceed the PATH_MAX
   limitation.  Otherwise, functions like `chdir' would fail with
   ENAMETOOLONG.

   FIXME-maybe: if find_dir_entry fails due to permissions, try getcwd,
   in case the unreadable directory is close enough to the root that
   getcwd works from there.  */

static void
robust_getcwd (struct file_name *file_name)
{
  size_t height = 1;
  struct dev_ino dev_ino_buf;
  struct dev_ino *root_dev_ino = get_root_dev_ino (&dev_ino_buf);
  struct stat dot_sb;

  if (root_dev_ino == NULL)
    error (EXIT_FAILURE, errno, _("failed to get attributes of %s"),
           quote ("/"));

  if (stat (".", &dot_sb) < 0)
    error (EXIT_FAILURE, errno, _("failed to stat %s"), quote ("."));

  while (1)
    {
      /* If we've reached the root, we're done.  */
      if (SAME_INODE (dot_sb, *root_dev_ino))
        break;

      find_dir_entry (&dot_sb, file_name, height++);
    }

  /* See if a leading slash is needed; file_name_prepend adds one.  */
  if (file_name->start[0] == '\0')
    file_name_prepend (file_name, "", 0);
}


/* Return PWD from the environment if it is acceptable for 'pwd -L'
   output, otherwise NULL.  */
static char *
logical_getcwd (void)
{
  struct stat st1;
  struct stat st2;
  char *wd = getenv ("PWD");
  char *p;

  /* Textual validation first.  */
  if (!wd || wd[0] != '/')
    return NULL;
  p = wd;
  while ((p = strstr (p, "/.")))
    {
      if (!p[2] || p[2] == '/'
          || (p[2] == '.' && (!p[3] || p[3] == '/')))
        return NULL;
      p++;
    }

  /* System call validation.  */
  if (stat (wd, &st1) == 0 && stat (".", &st2) == 0 && SAME_INODE(st1, st2))
    return wd;
  return NULL;
}


int
main (int argc, char **argv)
{
  char *wd;
  /* POSIX requires a default of -L, but most scripts expect -P.  */
  bool logical = (getenv ("POSIXLY_CORRECT") != NULL);

  initialize_main (&argc, &argv);
  set_program_name (argv[0]);
  setlocale (LC_ALL, "");
  bindtextdomain (PACKAGE, LOCALEDIR);
  textdomain (PACKAGE);

  atexit (close_stdout);

  while (1)
    {
      int c = getopt_long (argc, argv, "LP", longopts, NULL);
      if (c == -1)
        break;
      switch (c)
        {
        case 'L':
          logical = true;
          break;
        case 'P':
          logical = false;
          break;

        case_GETOPT_HELP_CHAR;

        case_GETOPT_VERSION_CHAR (PROGRAM_NAME, AUTHORS);

        default:
          usage (EXIT_FAILURE);
        }
    }

  if (optind < argc)
    error (0, 0, _("ignoring non-option arguments"));

  if (logical)
    {
      wd = logical_getcwd ();
      if (wd)
        {
          puts (wd);
          exit (EXIT_SUCCESS);
        }
    }

  wd = xgetcwd ();
  if (wd != NULL)
    {
      puts (wd);
      free (wd);
    }
  else
    {
      struct file_name *file_name = file_name_init ();
      robust_getcwd (file_name);
      puts (file_name->start);
      file_name_free (file_name);
    }

  exit (EXIT_SUCCESS);
}

```

---

### Post by fenerista on 2009-12-12
i found to how print process list 
```

  /* ProcessList.c 
    Robert Love Chapter 3
    */
    #include < linux/kernel.h >
    #include < linux/sched.h >
    #include < linux/module.h >

    int init_module(void)
    {
    struct task_struct *task;
    for_each_process(task)
    {
    printk("%s [%d]\n",task->comm , task->pid);
    }
   
    return 0;
    }

   
    void cleanup_module(void)
    {
    printk(KERN_INFO "Cleaning Up.\n");


    }
```

probably there is a simple way like this to print current folder name

---

### Post by grayrainbow on 2009-12-12
Sorry! I completely missunderstand you first time. So you want to print cwd of whatever process on the machine from another program. Does struct task_struct has something about filesystem state?

---

### Post by fenerista on 2009-12-12
> **grayrainbow said:**
> Sorry! I completely missunderstand you first time. So you want to print cwd of whatever process on the machine from another program. Does struct task_struct has something about filesystem state?

No, It is just an example my module isn't about proceses. I want to make a module like that. my module will be simple and exactly like pwd.

if my module is a proc I write console cat /proc/my_Pwd it will write current directory, It is very simple. Whatever, these not important How can I get the current directory on a module I think  get_cwd function  can't use in a module? and I don't know what exactly getcwd makes for me.

---

### Post by era86 on 2009-12-12
So the trick is to do a recursive call to something like pwd_helper().  This guy will recurse up all the way to the root.  Once it hits root, it will  print the current directory and return.

The trick is getting the parent directory of the current folder (file) you are in.  Now I know there are certain built in structs you can use to access the inode, the file, etc.  But that is the basic pattern I'm sure.

Someone posted a copy of the pwd call, might you take a look at that?  It uses the basename() function to do some of the heavy work.

---

### Post by fenerista on 2009-12-12
> **era86 said:**
> So the trick is to do a recursive call to something like pwd_helper().  This guy will recurse up all the way to the root.  Once it hits root, it will  print the current directory and return.

The trick is getting the parent directory of the current folder (file) you are in.  Now I know there are certain built in structs you can use to access the inode, the file, etc.  But that is the basic pattern I'm sure.

Someone posted a copy of the pwd call, might you take a look at that?  It uses the basename() function to do some of the heavy work.

I will look that.But where is the post can you give the link ? and "Now I know there are certain built in structs you can use to access the inode, the file, etc." can you write these here or a link?

and if we make my module simple, it just prints the current directory not to the root, how can i do that?

---

### Post by grayrainbow on 2009-12-12
I'm afraid you won't get something as simple as you hope, or at least I'm not aware of such a solution. You could look in kernel source(grep -in 'syscall_define.*getcwd' "kernel_source_directory" -r) how getcwd system call is implemented, and try to make something similar.

---

### Post by jpkotta on 2009-12-12
> **fenerista said:**
> No, It is just an example my module isn't about proceses. I want to make a module like that. my module will be simple and exactly like pwd.

if my module is a proc I write console cat /proc/my_Pwd it will write current directory, It is very simple. Whatever, these not important How can I get the current directory on a module I think  get_cwd function  can't use in a module? and I don't know what exactly getcwd makes for me.

This makes it sound like you want to get "the cwd of the module".  That doesn't make sense.  Modules are not processes, they're blobs of code that can be loaded into a running kernel.  It's like asking the cwd of the kernel, because modules are part of the kernel.  You can start processes from modules (and do basically anything else).  Sorry if I misinterpreted you.

EDIT:
I think the cwd of a process is in task->fs->pwd, where *task is the struct task_struct of the process.  See [http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371](http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371), [http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6](http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6), and [http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150](http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150).  This is where it comes from in /proc/*PID*/cwd.

---

### Post by grayrainbow on 2009-12-13
> **jpkotta said:**
> This makes it sound like you want to get "the cwd of the module".  That doesn't make sense.  Modules are not processes, they're blobs of code that can be loaded into a running kernel.  It's like asking the cwd of the kernel, because modules are part of the kernel.  You can start processes from modules (and do basically anything else).  Sorry if I misinterpreted you.

EDIT:
I think the cwd of a process is in task->fs->pwd, where *task is the struct task_struct of the process.  See [http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371](http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371), [http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6](http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6), and [http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150](http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150).  This is where it comes from in /proc/*PID*/cwd.
Actually modules are not so different. Just like user space programs they are peaces of code which are loaded and scheduled by the kernel, but run in kernel space and lot of stuff from user land are not quite appropriate for them, and since it will be close to the hardware it's good one to be more careful when writing them. I think OP could try follow
```
task->fs->pwd->whateverfollows
```
from post above, to something like char*, and call printk on it, but again, not sure how many precautions(that will be the tricky part) should be taken for such a access to file system structs.

---

### Post by jpkotta on 2009-12-13
> **grayrainbow said:**
> Actually modules are not so different. Just like user space programs they are peaces of code which are loaded and scheduled by the kernel, 

They're really not "like a program".  A module is essentially the same as a .o or a .so in userspace (hence the .ko extension), with the addition of load and unload hooks (init_module() and cleanup_module()).

---

### Post by fenerista on 2009-12-13
> **jpkotta said:**
> This makes it sound like you want to get "the cwd of the module".  That doesn't make sense.  Modules are not processes, they're blobs of code that can be loaded into a running kernel.  It's like asking the cwd of the kernel, because modules are part of the kernel.  You can start processes from modules (and do basically anything else).  Sorry if I misinterpreted you.

EDIT:
I think the cwd of a process is in task->fs->pwd, where *task is the struct task_struct of the process.  See [http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371](http://fxr.watson.org/fxr/source/include/linux/sched.h?v=linux-2.6#L1371), [http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6](http://fxr.watson.org/fxr/source/include/linux/fs_struct.h?v=linux-2.6#L6), and [http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150](http://fxr.watson.org/fxr/source/fs/proc/base.c?v=linux-2.6#L150).  This is where it comes from in /proc/*PID*/cwd.

No I can't tell any body what I want to do :) I should study english :, I want to get current directory name or path that I am at(it is the directory that is wrote on console that i am writing on) I know it is unnecessary but that's a home work.

don't add process to my problem :)

just I want that

If I am in this situtation 

[IMG]http://www.imagenic.net/images/n7rfllcj4igxl5ltrta4.jpg[/IMG]

and if I write to console cat /proc/mymodule

it will write "home/baron" or just "baron"

If I am in this situtation 

[IMG]http://www.imagenic.net/images/17mlfkddl443l8xs3gov.jpg[/IMG]
and if I write to console cat /proc/mymodule

it will write "/home/baron/ozel/hla" or just hla

and if you write console pwd sure it will write "/home/baron/ozel/hla" I want a module whose job is same as pwd.

it's not important the module is proc, device driver, or normal module. I want the function/functions whatever that gives me the current directory or path.

But you gave good informations to me. thx for that,  and I am looking them

---

### Post by grayrainbow on 2009-12-13
> **jpkotta said:**
> They're really not "like a program".  A module is essentially the same as a .o or a .so in userspace (hence the .ko extension), with the addition of load and unload hooks (init_module() and cleanup_module()).
Hmm, yea, that's what you say is true. And I'm not sure, but I think that init_module will run in space of the process which call insmod, in which case pwd(during insmod) for module should be pwd of insmod caller. And probably quite similar for all module functions, but with one exception - you can make kernel thread, and since Linux represent threads not much different than processes, this thread will be quite similar to 'normal' process,  but in kernel space, with task_struct available to be managed by the module itself, and I have no idea what will happen with that thread if its creator is rmmod(or probably you won't be able to rmmod it).

---

### Post by fenerista on 2009-12-13
I can't believe,  pwd is such a complex thing.

---

