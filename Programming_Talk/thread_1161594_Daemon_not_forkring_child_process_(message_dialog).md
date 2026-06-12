---
title: "Daemon not forkring child process (message dialog) on optimized Hi Guys, I am stuck"
date: 2009-05-16
forum: Programming Talk
---

### Post by alibaba163 on 2009-05-16
Daemon not forkring child process (message dialog)  in release mode

Hi Guys,

I am stuck with very strange problem. I have developed a daemon on ubuntu 8.10. This daemon is written in C using kdevelop (as IDE).

This daemon launches itself on system boot and connects to Gateway on Windows operating system. The work of daemon is very simple it just forks a child process whenever request is send from gateway on windows.

On Forking the process, deamon simply launches a dialog build in gtkmm using kdevelop. The dialg( a notification) reside at /usr/nsn/gui/message/.

Daemon performs differently with debug and release mode

ON RELEASE MODE (OPTIMIZED MODE):

The problem is that daemon works absolutely fine when I start the daemon from terminal, using following command
sudo /etc/init.d/notifydaemon (name of daemon is notifydaemon)

But it does'nt lauch the child process when system is rebooted. Daemon does get started and I can see the daemon in ps aux | grep notifydaemon
but it does not launch the dialog.

All the variable values are fine since I have debugged the code by writing values in log files. however, same daemon performs perfect while running in debug mode

ON DEBUG MODE:

Same daemon works absolutely fine in debug mode. It lauches the dialog on /usr/nsn/gui/message when I start daemon from terminal

Also it launches the dialog when system is rebooted.


Peace of code which launches the dialog is given below

pid_t ForkGuiProcess(const char * directory, const char * command, char ** putenvs)
{
std::string path (directory);
path += "/";
path += command;


pid_t pid = ::fork();
if(pid == -1)
{

nsm::Log ("Couldn't fork UI Process");
// Horrible error
return -1;
}
else if(pid != 0)
{
return pid;
}
else
{

//nsm::Log ("Forked UI process");


// If root, spoof the current UI user
if (::geteuid () == 0)
{

}
//nsm::Log(::getenv("XAUTHORITY"));
//nsm::Log(::getenv("DISPLAY"));
//nsm::Log(path);

// Set any environment variables the user wants us to
if (putenvs != NULL)
{
while (*putenvs != NULL)
{
putenv(*putenvs);
putenvs++;
}
}


// Run the command
char * args[] = {(char *)path.c_str(), NULL};
int err = ::execv(path.c_str(), args);
if (err != 0)
{
nsm::Log("Error launching child process");
std::exit(1);
}
}
return pid;
}

}


Please help!!!!!!!!!!!!!!

Thanks.

Alibaba.

---

### Post by dwhitney67 on 2009-05-16
I'm sure your code is fine (although, to be honest, I did not peruse it too closely).  I suspect that the dialog box cannot appear unless a window-manager (e.g. gnome) is already running.

If you launch the daemon during boot-up, a window-manager is not running until you log in.  It is probably because of this that your dialog exits immediately after it is launched.

Within your daemon, check if this is the case (by checking the exit status).  If so, periodically attempt to relaunch the dialog until the daemon is successful in doing so; or alternatively, check that there is a window-manager running before attempting to launch the dialog.

---

### Post by alibaba163 on 2009-05-17
Hello,
      Thanks alot for your reply. My display manager is "gdm". My window manager is actually running because I am trying to launch the dialog AFTER I HAVE LOGGED INTO THE SESSION.

Also I can testify that by running xeyes. If I type xeyes on shell then it successfully lauches the "xeyes window". And If I type gdm on shell it does diplay that gdm is running.


Also after I login (after system reboot).And then if I restart the daemon by using following command sudo /etc/init.d/notifydaemon restart (notifydaemon is my own script placed at /etc/init.d) then again my daemon would successfully launch the dialog.

The only problem is that it cannot launch the dialog after login (at system reboot). 

Any help wold be greatly appreciated..

Thanks.

alibaba

---

### Post by dwhitney67 on 2009-05-17
> **alibaba163 said:**
> 
Also after I login (after system reboot).And then if I restart the daemon by using following command sudo /etc/init.d/notifydaemon restart (notifydaemon is my own script placed at /etc/init.d) then again my daemon would successfully launch the dialog.

Of course; this is what I would expect.

> **alibaba163 said:**
> 
The only problem is that it cannot launch the dialog after login (at system reboot).

During boot-up, the daemon failed to launch the dialog.  Once again, this is expected because a window-manager is not running at this point.  It is only _after_ you login, then relaunch the daemon that the dialog appears.

P.S.  gdm is not a window manager.

---

### Post by alibaba163 on 2009-05-17
> **dwhitney67 said:**
> Of course; this is what I would expect.


During boot-up, the daemon failed to launch the dialog.  Once again, this is expected because a window-manager is not running at this point.  It is only _after_ you login, then relaunch the daemon that the dialog appears.

P.S.  gdm is not a window manager.

Sorry, I think I did'nt explain what I was trying to ask. First thing we need to know is that daemon will never be able to launch the dialog during boot up time (since this is not what I want). Daemon will only launch the dialog when a message will be sent to it from a server(a small application that sends a dialog message) running on windows vista.

Now server application on windows vista  will only be able to see the daemon connected to it when I login to gnome session, It will never see the daemon during boot up time (sinces daemon has to connect to server app. and it can only connect once user logs in to gnome session)


And apologies again yes you are right gdm is not windows manager. My windows manager is metacity which I can see running in system monitor after login.

Regards

Alibaba.

---

### Post by dwhitney67 on 2009-05-17
The only other thing I can think of is that you would need to export the definition of DISPLAY so that the daemon knows where to launch the dialog.

The best thing to do right now is to determine why the dialog does not appear.  Surely there must be a return code or other diagnostic message that is returned when the dialog fails to appear.

---

### Post by alibaba163 on 2009-05-18
> **dwhitney67 said:**
> The only other thing I can think of is that you would need to export the definition of DISPLAY so that the daemon knows where to launch the dialog.

The best thing to do right now is to determine why the dialog does not appear.  Surely there must be a return code or other diagnostic message that is returned when the dialog fails to appear.

I am already export display (0.0) in the code, that is the reason why daemon lauches the dialog using debug verson. 

Now what I am trying to do is to launch simple xeyes using system api

i.e  int err = system("xeyes");

no the return code here is -1 which is the normal execution behaviour for system API. Now I beleive its launching the dialog ( on release version). Daemon does not seem to have the right priviliges to launch the window when I use release version. 

Any idea???

Regards,

Alibaba.

---

### Post by dwhitney67 on 2009-05-18
As for the issues you are having, I suspect that even though you are setting the DISPLAY, your application still is unable to open it.

I developed a simple app, which runs as expected when I am logged in and I am the user running it, but when I attempt to run it as 'root', it fails to launch because of the DISPLAY issue.

Here's my app:
```

#include <cstdlib>
#include <cassert>
#include <string>
#include <iostream>

void launchGui(const char* dir, const char* cmd, char** putenvs)
{
  std::string path(dir);
  path += "/";
  path += cmd;

  pid_t pid = fork();

  if (pid == 0) {
    // child...
    if (putenvs) {
      while (*putenvs != 0) {
        putenv(*putenvs);
        ++putenvs;
      }
    }

    char* args[] = { const_cast<char*>(path.c_str()), 0 };

    execv(path.c_str(), args);

    // we will never be here, unless execv() fails.
    std::cerr << "Child failed to launch '." << path << "'" << std::endl;
  }
}

int main()
{
  char* penvs[] = { const_cast<char*>("DISPLAY=:0.0"), 0 };

  launchGui("/usr/bin", "xeyes", penvs);
}

```

To build/run:
```

g++ launchGui.cpp -o launchGui
./launchGui

```

Now, when I log in as root from a terminal, and run the same command, it fails because of the DISPLAY issue.

If you feel that I have missed setting an important environment variable, please let me know so that I can update my code and retest.

---

