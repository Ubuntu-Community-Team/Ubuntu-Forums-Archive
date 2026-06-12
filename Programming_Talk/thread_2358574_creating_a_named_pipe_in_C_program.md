---
title: "creating a named pipe in C program"
date: 2017-04-14
forum: Programming Talk
---

### Post by jlw2002us on 2017-04-14
How can I create a named pipe in c? My program that's creating the pipe is in the test directory.

I have:

```
   char * mypipe = "/test/mypipe";

  if(mkfifo(mypipe,0666)==-1)
  {
      if(errno != EEXIST)
      {
         perror("Fatal Error:  ");
         exit(0);
       }
  }

```
I keep getting "Fatal Error" when I run the program.

---

### Post by TheFu on 2017-04-14
Does the directory /test/ exist?
Does the userid have write access to create a file inside the /test/ directory?

Please post a small, but complete program showing what you intend.  What is posted above doesn't compile. Where is errno assigned - and where is it declared?

BTW, google found this answer: [https://stackoverflow.com/questions/2784500/how-to-send-a-simple-string-between-two-programs-using-pipes](https://stackoverflow.com/questions/2784500/how-to-send-a-simple-string-between-two-programs-using-pipes)

---

### Post by jlw2002us on 2017-04-15
I'm having success with creating a pipe in the same directory as the program that creates it.  But I can't write to the pipe even with full permissions turned on.

---

### Post by TheFu on 2017-04-15
Sounds like some normal Unix permissions knowledge is needed. Would you agree?

There are lots of tutorials for that - google finds them. In my Linux training classes, I get the students to spend 45 minutes with 3 userids and 5 groups just playing around with different permissions and grouping until the light goes off in their heads. Once that happens, this sort of issue will never happen again.

---

### Post by jlw2002us on 2017-04-15
User has read/permissions. Group has read.  Other has read.  Are more permssions needed?  It just keeps getting "stuck" when I run the program.



char *mypipe = ("mypipe");
mkfifo(mypipe, 0666);
fdw = open("mypipe",O_WRONLY);
if (fdw < 0)
{
  perror("File can't open to write.");
  return;
}
int b;
b=3;
write(fdw,&b,sizeof(b));
close(fdw);


Program 2:
int fdl;
int data;
fdl = open("mypipe",O_RDONLY);
if ( fdl < 0)
{
  perror("File can't open to read.");
  return;
}
read(fdl,&data,sizeof(data));
close(fdl);

---

### Post by TheFu on 2017-04-15
The writing program must have write access. Read is not sufficient. Write is required on the directory or the file won't be created.

Rather than explaining permissions, please just show the **ls -l** output. That prevents confusion (on both sides).

---

