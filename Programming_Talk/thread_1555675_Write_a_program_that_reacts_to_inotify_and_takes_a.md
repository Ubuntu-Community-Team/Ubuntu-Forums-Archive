---
title: "Write a program that reacts to inotify and takes arguments"
date: 2010-08-18
forum: Programming Talk
---

### Post by Zilioum on 2010-08-18
The last two days I have been writing a little program in c++ that takes the name of an .mkv file as an argument and then converts it to an .mp4. Now that it works well, I want to automate the whole process. For this I want to write a second program or scripts that starts my other program on the newly created (hum, downloaded) files. I've been playing around with inotifywait for a bit and I got it to work without trouble. The point were I'm hitting a wall, is were I have to feed the information of were the file has been created and what it's name is to my program. The main problems I have are these:
[LIST]
[*]I need inotifywait to run with -m (continuous). Because otherwise, if multiple files are created, it only generates a message for the first one, and then exists.
[*]Using popen() or shell scripts didn't work, because they wait for inotifywait to terminate, which never happens. And for some reason, popen() doesn't read the output of inotifywait, even if it terminates (without -m).
[/LIST]


I cant think of another way how to do this and my way clearly doesn't work. So I'm hoping on some ideas on how to resolve this problem. It doesn't have to be with the tools I used up to now, any input is appreciated.

Cheers

---

### Post by Zugzwang on 2010-08-18
> **Zilioum said:**
> Using popen() or shell scripts didn't work, because they wait for inotifywait to terminate, which never happens. And for some reason, popen() doesn't read the output of inotifywait, even if it terminates (without -m).


That shouldn't be the case. I suspect that you have some other problem in your program. The "popen" command does explicitly *not* wait for the child to terminate. Here's an example:

[PHP]
#include <stdio.h>
#include <iostream>

int main() {
    FILE *f = popen("sleep 10", "r");
    if (f == NULL) {
        std::cout << "Cannot open command" << std::endl;
        return 1;
    }

    std::cout << "Waiting for the process to terminate" << std::endl;

    int s = pclose(f);
    if (s == -1) {
        std::cout << "Error occurred!" << std::endl;
        return 1;
    }

    std::cout << "All ok!" << std::endl;
    return 0;
}
[/PHP]

When running the program, you will see that the waiting line pops up (almost) immediately while the "All ok" line only pops up after 10 seconds, i.e., after the process has been terminated.

---

### Post by Zilioum on 2010-08-19
> That shouldn't be the case. I suspect that you have some other problem in your program. The "popen" command does explicitly *not* wait for the child to terminate.
That might very well be. But my problem is that I haven't found a way to continuously monitor the output of inotifywait and then process it further (convert the newly created files). 
Here's the code I used to get some info about the file. It runs mkvinfo on the file (name is passed by argument) and then gives me back the result as a string. I'm trying to get something similar for inotifywait, with the exception that the monitoring should be continuous.
[PHP]
string extract::info(string name)
{

	string command = "mkvinfo ";

	command.append(name);
	FILE* fp;
	char result[6000];
	fp = popen(command.c_str(), "r");
	fread(result, 1, sizeof(result), fp);
	fclose(fp);

	string info(result);

	return info;
}[/PHP] 
The code above works well. So I tried the same with a inotifywait command.
[PHP]
int
main( int argc, const char* argv[] )
{
	string command = "inotifywait -r -e create --format '%w %f' /media/mediadisk/files";

		FILE* fp;
		char result[6000];
		fp = popen(command.c_str(), "r");
		fread(result, 1, sizeof(result), fp);
		fclose(fp);

		string info(result);

		cout << info << "test" << endl;

		return 0;
}
[/PHP]
And this doesn't work: If I created multiple files at the same time I would only be notified of the first one, so this should work continuously. And strangely enough, as soon as a file is created the only output is "test". The string "info" is empty I guess.

I'm just not sure if what I'm doing at the moment is the right way. There has to be a way to solve this, this is Linux :D

---

### Post by dwhitney67 on 2010-08-19
Why are you calling the shell from your C++ application?  If you had done the proper research, you would have found that similar notification tools are available for C++/C programs.

Here's a basic example that is lacking proper error checking at every corner, but hey, the program works under ideal conditions.
```

#include <sys/inotify.h>
#include <sys/ioctl.h>
#include <iostream>

void processNewFiles(int fd, int wd);


int main(int argc, char** argv)
{
   const char* dirPath = argv[1];

   int fd = inotify_init();
   int wd = inotify_add_watch(fd, dirPath, IN_CREATE);

   if (wd)
   {
      processNewFiles(fd, wd);

      inotify_rm_watch(fd, wd);
   }
}


void processNewFiles(int fd, int wd)
{
   bool done = false;

   do
   {
      int qLen = 0;

      ioctl(fd, FIONREAD, &qLen);

      char* buf = new char[qLen];
      int   num = read(fd, buf, qLen);

      if (num == qLen)
      {
         inotify_event* iev = reinterpret_cast<inotify_event*>(buf);

         if (iev->wd == wd && iev->mask & IN_CREATE)
         {
            std::cout << "New file created: " << iev->name << std::endl;
         }
      }

      delete [] buf;
   } while (!done);
}

```

P.S.  Consider adding a signal handler that will handle common signals, such as SIGTERM and SIGINT, so that you can exit the program gracefully.

---

### Post by splicerr on 2010-08-19
> **Zilioum said:**
> 
[PHP]
    fp = popen(command.c_str(), "r");
    fread(result, 1, sizeof(result), fp);
    fclose(fp);
[/PHP][PHP]
        fp = popen(command.c_str(), "r");
        fread(result, 1, sizeof(result), fp);
        fclose(fp);
[/PHP]

I don't know about the rest of your code. But if your program mainly consists of executing other programs and gluing them together with some logic, then you're using the wrong tool for the job. Shell scripts are much more suitable for that.

---

### Post by Zilioum on 2010-08-19
> Why are you calling the shell from your C++ application? If you had done the proper research, you would have found that similar notification tools are available for C++/C programs.
The code I posted was from my program I wrote to do the conversion. There it was the only way to do what I wanted to do. The problem I had, is that I didn't know what to look for.
But I think your code might do the trick, will give it a shot as soon as I have time, thanks a lot.

> I don't know about the rest of your code. But if your program mainly consists of executing other programs and gluing them together with some logic, then you're using the wrong tool for the job. Shell scripts are much more suitable for that.
I tried doing it with a shell script, but I ran into the same problem as with my c++ equivalent: Not being able to monitor the output continuously.

---

### Post by soltanis on 2010-08-19
I've done something very similar to this using a shell script and pipes.

```

inotifywait -m -e close_write --format "ffmpeg -i ${indir}/%f ${outdir}/%f.mp3" "$indir" | sh

```

inotifywait lets you specify format strings, so if you bend them a little bit (in this example, having them write shell commands that are piped into a shell instance), you can do basically anything you want (the only limit is that inotifywait specifies the format string can only be around 4000 characters long, after which it gets truncated).

If you intend to do this from a larger C/C++ application you should use the actual [inotify]("http://dell9.ma.utexas.edu/cgi-bin/man-cgi?inotify+7") interface to do it, since inotifywait is really just a wrapper around Linux filesystem hooks.

---

### Post by Zilioum on 2010-08-19
> **soltanis said:**
> I've done something very similar to this using a shell script and pipes.

```

inotifywait -m -e close_write --format "ffmpeg -i ${indir}/%f ${outdir}/%f.mp3" "$indir" | sh

```

inotifywait lets you specify format strings, so if you bend them a little bit (in this example, having them write shell commands that are piped into a shell instance), you can do basically anything you want (the only limit is that inotifywait specifies the format string can only be around 4000 characters long, after which it gets truncated).

If you intend to do this from a larger C/C++ application you should use the actual [inotify]("http://dell9.ma.utexas.edu/cgi-bin/man-cgi?inotify+7") interface to do it, since inotifywait is really just a wrapper around Linux filesystem hooks.

Sounds interesting as well, and I like the idea of piping the command into a shell instance. Thanks a lot for the input.
Will have a look at all this over the weekend :D

---

