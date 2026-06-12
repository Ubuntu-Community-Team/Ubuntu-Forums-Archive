---
title: "Linux API Reference [urgent]"
date: 2008-08-26
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-08-26
Hi guys,
I'm going to write a program in Linux and I need some API function, but I can't find a reference for Linux (similar to MSDN in Windows) !!! I know that I can for example log off a user in command line with skill, pkill but I want to do with API functions. Now I need get user home directory, logged on user name, reboot the system, kill a process and ...
After that I have to learn forks, NTPL, sockets, ...
Any Reference, help, tutorial, Documentation ... ?
Thanks for your considerations :KS

---

### Post by nvteighen on 2008-08-26
Have you installed the "linux-doc" package from the repos? It will install references to the last kernel version into /usr/share/doc/linux-doc-<kernel version>.

---

### Post by cmay on 2008-08-26
[http://linux.die.net/man/3/getpwuid_r](http://linux.die.net/man/3/getpwuid_r)
i dont know if that is what you look for.
hope it helps anyway.

---

### Post by hosseinyounesi on 2008-08-26
Thanks,
But let me ask my questions in more detail : 
NOW, I want to get the computer_id, logged on usernameS, and do some commands like reboot, shut down, log off, kill a process and commands like these. Any one help me ? I found this commands in MSDN, but not yet for linux :(

---

### Post by signifer123 on 2008-08-26
> **hosseinyounesi said:**
> Thanks,
But let me ask my questions in more detail : 
NOW, I want to get the computer_id, logged on usernameS, and do some commands like reboot, shut down, log off, kill a process and commands like these. Any one help me ? I found this commands in MSDN, but not yet for linux :(

They have books for like $3 at borders with common linux commands. Presonally i'm a scripter though so commands are what i use.

computer_id? hostname - try the `hostname` command
logged on users - try `users` command, or `who`
shutdown = `shutdown -h -P now`, or `poweroff`, or `runlevel 0`
reboot = `reboot`, or `runlevel 6`
kill a proccess = `kill proccessid`, or `killall processname`
get home = just filters through `env`

as for the api, as was mentioned before. [http://linux.die.net/man/](http://linux.die.net/man/).

You probably want the 2 or 3 parts.

like hostname is gethostname()

---

### Post by hosseinyounesi on 2008-08-26
Thanks,
You helped me a lot. I want to use these commands in C++ !!!
Please do not tell me to use system("") ! I want to use LINUX API :) Any advanced Linux programmer here ???
Thanks for your help

---

### Post by DrMega on 2008-08-26
> **hosseinyounesi said:**
> Thanks,
You helped me a lot. I want to use these commands in C++ !!!
Please do not tell me to use system("") ! I want to use LINUX API :) Any advanced Linux programmer here ???
Thanks for your help

A long while ago, I raised the point that the distinct lack of a Linux API was one of the things that held Linux back. There followed a torrent of postings explaining why it would be a bad idea to have a stable and consistent API for Linux. As a Windows developer I couldn't understand the reasons why an API was a bad idea, so we all had to agree to disagree and accept that our disagreement was an example of the individuality and uniqueness that makes Linux great.

So, good luck. I'll keep an eye on this thread, you may get further than I did:)

---

### Post by cmay on 2008-08-26
[http://www.opengroup.org/onlinepubs/000095399/download/](http://www.opengroup.org/onlinepubs/000095399/download/)
i once found this ? you can download it.

there is examples like this thats gets login name.

[PHP]
#include <unistd.h>
#include <sys/types.h>
#include <pwd.h>
#include <stdio.h>
#include <stdlib.h>
int main()
{
char *lgn;
struct passwd *pw;
if ((lgn = getlogin()) == NULL || (pw = getpwnam(lgn)) == NULL)
  {
    fprintf(stderr, "Get of user information failed.\n");
    exit(1);
    }
    printf("hello your login is %s",getlogin());
    return 0;
}
[/PHP]
i cant help anymore than this .i am not an advanced linux programmer.

---

### Post by hosseinyounesi on 2008-08-26
Thanks but I think that getlogin() returns just the username that runs this program not the all 7 linux terminals ?!!!

---

### Post by signifer123 on 2008-08-26
Okay. API, you can get HOME directory with getenv("HOME"), username with getenv("USERNAME"). Both are part of the cstdlib(#include <stdlib.h>). 

Killing a proccess, you use kill(pid_t pid, int sig);(#include <sys/types.h>#include <signal.h>) The signal you want is probably 15.

You use kill to send more signals too. 
For reboot, you send init(A.K.A. process 1), signal 18 or Terminal Stop. so kill(1,18);, which will prevent it from creating more apps, you may need to kill everything else though to complete a reboot.
For shutdown you use signal 2, kill(1,2);

To logoff a user, you find the processes that they are running, and kill them all, it will kick them out of the Xsession and back to the login screen. From what i've looked at killpg(getsid(processTheyAreUsing));(#include <signal.h>)

For the ones that shutdown, you may want to call sync();(#include <unistd.h>).

I attached a sample of a logoff, user list with the base for getting info, and reboot.

The USR2 signal the documentation said would poweroff the computer didn't work for me, so there isn't a shutdown. And the reboot uses signal 2, instead of the above mentioned one. 

The logoff also doesn't log that the user was logged off, it just forces them off.

---

### Post by hod139 on 2008-08-26
You can browse around here: 
[http://ldn.linuxfoundation.org/](http://ldn.linuxfoundation.org/)

---

### Post by jinksys on 2008-08-26
There's a book called Advanced Programming in the UNIX Environment that contains a lot of good information.  Use two hands to read it, it's huge.

---

### Post by hosseinyounesi on 2008-08-27
Thanks a lot signifer, I got what you want to say. I'm going to do that and I'll report what I done here :) And I will post whatever else I learned.
Thanks again

---

### Post by hosseinyounesi on 2008-08-27
Hi again, There is a problem in signifer ListUser file. He is looking in utmp file ! Is there any other way ? And also he doesn't consider the log out so if I login in a terminal and log out again, program will list this user too !!! What I have to do ?
But there is no problem in logout file, but it doesn't log the logout. It can be repaired by this function :

write_wtmp(char *user, char *id, int pid, int type, char *line);

I can help more about this function, if you want.

---

### Post by mssever on 2008-08-27
There is no single API. A Linux system is a combination of many different projects, each of which has its own APIs or other ways of working with the system. (Linux itself properly refers to the kernel, not the rest of the system.) So, there's no single source of documentation (other than Google :)).

---

### Post by MarkieB on 2008-08-27
no longer participating in ubuntuforums.org

---

### Post by hosseinyounesi on 2008-08-28
Hi again, Any one knows how to delete a file and folder in linux with c++ ? I did it in windows but linux is really annoying me ? 
Why there isn't any API reference ? Linux is really really really just working with files. Is that always good ? I have to read a file (wtmp or utmp) and get current loggedon username !!! It can slow down  my program :( Really there isn't other way ?

---

### Post by dwhitney67 on 2008-08-28
The easiest way is to use the unlink() library call.

To get the user's name:

[php]const char *username = getenv( "USERNAME" );[/php]

If you want to get all users that are logged in, use the command 'who'.  The only way I know of how to get this information is to use system() to issue the 'who'.

---

### Post by Zugzwang on 2008-08-28
> **hosseinyounesi said:**
> Hi again, Any one knows how to delete a file and folder in linux with c++ ? I did it in windows but linux is really annoying me ? 
Why there isn't any API reference ? Linux is really really really just working with files. Is that always good ? I have to read a file (wtmp or utmp) and get current loggedon username !!! It can slow down  my program :( Really there isn't other way ?

"unlink" or "remove" for files and "rmdir" and "remove" for directories. The reason why there is no reference is already stated above. You can however look at the POSIX standard for all standard operations. Also there is this page: [http://opengroup.org/onlinepubs/007908775/]("http://opengroup.org/onlinepubs/007908775/").

"Working with files" (I think that you mean accessing information via /proc/ or /dev/) is one of the main concepts in Linux. It allows you to explore the information/devices avaliable. It also allows fine-granular user access control for devices, for example. Since access to the /proc/ stuff is integrated into the kernel, it won't slow down you application much. In fact all the functions/information provided there is of a kind that you wouldn't need to poll it very often, so this is no big deal.

---

### Post by mssever on 2008-08-28
> **hosseinyounesi said:**
> Linux is really really really just working with files. Is that always good ?In Unix, everything is a file. That includes hardware, and kernel settings. See [*The Art of Unix Programming*]("http://www.catb.org/%7Eesr/writings/taoup/html/index.html").> I have to read a file (wtmp or utmp) and get current loggedon username !!!The environment variable $USER will give you the current username.

---

### Post by hosseinyounesi on 2008-08-29
Thanks every body. I decided to use "users" bash command but I don't want to use system() at all (in Linux or Windows). So the best way I could find is to use it's source code. Is it available ?
Is this included in open source ? getting host name is just like users ? any api or ... ?
Thanks for your consideration again, really good forum :)

---

### Post by hosseinyounesi on 2008-08-29
:ks

---

### Post by signifer123 on 2008-08-29
> **hosseinyounesi said:**
> Thanks every body. I decided to use "users" bash command but I don't want to use system() at all (in Linux or Windows). So the best way I could find is to use it's source code. Is it available ?
Is this included in open source ? getting host name is just like users ? any api or ... ?
Thanks for your consideration again, really good forum :)

Yeah, those are part of the GNU utils, they are definately OpenSource.

Users is part of core utilities. Along with a ton of other things

You can get the tarball here:
[http://www.gnu.org/software/coreutils/](http://www.gnu.org/software/coreutils/)

Just open it, and look at coreutils/src/users.c. 


<*sidenote>touch.c For something that just makes a new file it's 420 lines long...</*sidenote>

---

### Post by dwhitney67 on 2008-08-29
> **hosseinyounesi said:**
> Thanks every body. I decided to use "users" bash command but I don't want to use system() at all (in Linux or Windows). So the best way I could find is to use it's source code. Is it available ?
Is this included in open source ? getting host name is just like users ? any api or ... ?
Thanks for your consideration again, really good forum :)
Here's a simple program that can list the users that are logged into your system; it displays other information too, such as their tty or whether they are logged in from a remote host. 
[PHP]#include <utmp.h>
#include <iostream>

std::ostream& operator<<( std::ostream &os, const struct utmp *ut )
{
  os << '\n'
     << "ut_type = " << ut->ut_type << '\n'
     << "ut_pid  = " << ut->ut_pid  << '\n'
     << "ut_id   = " << ut->ut_id   << '\n'
     << "ut_user = " << ut->ut_user << '\n'
     << "ut_host = " << ut->ut_host;

  return os;
}

int main()
{
  struct utmp *ut = 0;

  do
  {
    if ( (ut = getutent()) != 0 )
    {
      std::cout << ut << std::endl;
    }
  } while ( ut != 0 );

  return 0;
}[/PHP]

P.S.  Run "man utmp" and "man getutent" for more information.

---

### Post by hosseinyounesi on 2008-08-30
Thanks, I changed your code in this one and it is now works well:

[PHP]setutent();
	struct utmp *ut = 0;
	long i=0;
	do
	{
		if((ut=getutent())!=0)
		{
			if(strcmp(ut->ut_user,"LOGIN")!=0 && strcmp(ut->ut_user,"runlevel")!=0)
			{
				if(strcmp(ut->ut_user,"")!=0 && ut->ut_id[0]!='/')
				{
					strcpy(username[i],ut->ut_user);
					strcpy(userTerminal[i],ut->ut_line);
					userPID[i]=ut->ut_pid;
					if(strcmp(ut->ut_line,":0")==0)
					// ":0" means X !!!
						strcpy(userTerminal[i],"tty7");
					i++;
				}
			}
		}
	}while(ut!=0);
	nums_of_users=i;
	endutent();[/PHP]

endutent() is used to set file pointer to the beginning. If you want to use this function more than one time in a program !!!

---

