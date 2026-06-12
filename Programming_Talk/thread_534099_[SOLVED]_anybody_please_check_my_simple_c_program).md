---
title: "[SOLVED] anybody please check my simple c program:)"
date: 2007-08-24
forum: Programming Talk
---

### Post by AlexenderReez on 2007-08-24
i want to create compiz installer using c language.....so i hope anybody can check it..i do realized there is[ bash script]("http://ubuntuforums.org/showthread.php?t=508769") ..but i aim to create this script for learning...and fun...so please check....

**i comment few things that i don't really sure**

ASSUMPTION ---

1.anybody want to install using this script already confirmed that they have all dependencies...
there is simple script for compiling...
> all: clean compile

compile:
	gcc -o install compizinstall.c
	
clean:
	rm -r -f compizinstall 
-->just run make in the directory..then ./compizinstall.c (which is name of this scpit file...

3.PLEASE IGNORE COMPIZ commands...because i try to build this scpit for fedora and ubuntu....i will figure out it afterward...

```
#include <stdio.h>
#include <string.h>

main() {
int choice=0, color=0;
char def[2000];           //determine buffer overflow
char user[2000];
char home[] = "/home/";        //move to home folder
FILE *username;

def[0]='@';
def[1]='@';

system ("whoami > /tmp/.user");    //user in /tmp/.user 
username = fopen ("/tmp/.user", "rb");
fscanf (username, "%s", user);          //check user privillege 
strcat (home, user);
fclose (username);
system ("rm /tmp/.user"); 
strcat (home, "/compiz");//not sure...anybody please check

printf ("\nThis is trial version compiz fusion installer");
printf ("\nit should suitable suite for Gnome.");

while (def[0]!='y' && def[0]!='n' || def[1]!='\0')   {               //do user want default process?
printf ("\nD'you wanna proceed with the default choice which is to install compiz? (y/n) ");
scanf ("%s", def);    
if (def[0]!='y' && def[0]!='n' || def[1]!='\0')   {  
printf("\nERROR: choice not valid!\n");             } } 

if (def[0]=='y') {                                            //if default
choice=1;       color=2; 
goto start;
}

printf("\nWhat d'you wanna do?\n");
printf("1) Install  compiz;\n");
printf("2) Upgrade compiz ;\n");
printf("3) Uninstall compiz ;\n");
printf("4) Exit\n\n");

//ask options
while (choice != 1 && choice !=2 && choice!=3) {         //other options
printf("Enter your choice: ");
scanf ("%d", &choice);
if (choice!=1 && choice!=2 && choice!=3) printf("\nERROR: choice not valid!\n");

}
if (choice==1) {          //install compiz:)

fputs("\nCreating compiz directory in home folder.............................. ", stderr);

system("rm -r -f ~/compiz");//make sure there is no compiz folder in home directory

system("mkdir ~/compiz && cd ~/compiz");//creating compiz folder
printf("done\n");
fputs ("Installation compiz using git repo..........................", stderr);

//system("");//removing all installed compiz package
system("sudo apt-get remove compiz*");
system("sudo apt-get remove emerald*");//also doesn't confirm it
system("git clone git://git.freedesktop.org/git/xorg/app/compiz && cd compiz && git checkout origin/compiz-0.6 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/libraries/bcop && cd bcop && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/ccsm && cd ccsm && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/libcompizconfig && cd libcompizconfig && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/compizconfig-python && cd compizconfig-python && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-main && cd plugins-main && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald && cd emerald && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald-themes && cd emerald-themes && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/users/crdlb/fusion-icon");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-extra && cd plugins-extra && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-unsupported && cd plugins-unsupported && git checkout origin/0.6.0 && cd ~/compiz");
printf("done git commands..next is to install it\n");

fputs ("installation................................................... ", stderr);
system("cd ~/compiz/compiz");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig");
system("cd ~/compiz/bcop");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/libcompizconfig");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/compizconfig-python");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-main");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/emerald");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/emerald-themes");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-extra");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-unsupported");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/ccsm");
//system("");
system("python setup.py install");
system("cd ~/compiz/fusion-icon");
system("make");
system("sudo make install");

//installation finished...
printf("done\n");
printf("\nOperation successfully completed.\n");
return 0;
	}
if (choice==2) {                      //upgrade compiz


fputs ("\nUpgrade start........................................................ ", stderr);
system("cd ~/compiz/compiz");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig");
system("cd ~/compiz/bcop");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/libcompizconfig");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/compizconfig-python");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-main");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/emerald");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/emerald-themes");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-extra");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install");
system("cd ~/compiz/plugins-unsupported");
system("git pull origin 0.6.0");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/ccsm");
system("git pull origin 0.6.0");
system("su -");
system("python setup.py install");
system("cd ~/compiz/fusion-icon");
system("git pull origin 0.6.0");
system("make");
system("make install");
printf("\nUpgrade successfully completed.\n");
return 0;
} 

if (choice==3){
fputs ("Removing compiz................................................... ", stderr);
system("cd ~/compiz/compiz");
system("make uninstall");
system("cd ~/compiz/bcop");
system("make uninstall");
system("cd ~/compiz/libcompizconfig");
system("make uninstall");
system("cd ~/compiz/compizconfig-python");
system("make uninstall");
system("cd ~/compiz/plugins-main");
system("make uninstall");
system("cd ~/compiz/emerald");
system("make uninstall");
system("cd ~/compiz/emerald-themes");
system("make uninstall");
system("cd ~/compiz/plugins-extra");
system("make uninstall");
system("cd ~/compiz/plugins-unsupported");
system("make uninstall");
system("cd ~/compiz/ccsm");
system("make uninstall");
system("cd ~/compiz/fusion-icon");
system("make uninstall");
printf("\nRemoving successfully completed.\n");

}

if (choice==4) return 0;           //exit

//just default..same with option 1

start:      //mark start default upgrade
{
fputs("\nCreating compiz directory in home folder.............................. ", stderr);

system("rm -r -f ~/compiz");//make sure there is no compiz folder in home directory
system("mkdir ~/compiz && cd ~/compiz");//creating compiz folder
printf("done\n");
fputs ("Installation compiz using git repo..........................", stderr);

system("su -");//removing all installed compiz package
system("yum remove compiz*");//not sure whether yum can do it...it works for apt(debian)
system("yum remove emerald*");//also doesn't confirm it
system("git clone git://git.freedesktop.org/git/xorg/app/compiz && cd compiz && git checkout origin/compiz-0.6 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/libraries/bcop && cd bcop && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/ccsm && cd ccsm && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/libcompizconfig && cd libcompizconfig && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/compizconfig/compizconfig-python && cd compizconfig-python && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-main && cd plugins-main && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald && cd emerald && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald-themes && cd emerald-themes && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/users/crdlb/fusion-icon");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-extra && cd plugins-extra && git checkout origin/0.6.0 && cd ~/compiz");
system("git clone git://anongit.compiz-fusion.org/fusion/plugins-unsupported && cd plugins-unsupported && git checkout origin/0.6.0 && cd ~/compiz");
printf("done git commands..next is to install it\n");

fputs ("installation................................................... ", stderr);
system("cd ~/compiz/compiz");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig");
system("cd ~/compiz/bcop");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/libcompizconfig");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/compizconfig-python");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/plugins-main");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/emerald");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/emerald-themes");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/plugins-extra");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/plugins-unsupported");
system("./autogen.sh --prefix=/usr/local --disable-kde && make && make install");
system("cd ~/compiz/ccsm");
system("su -");
system("python setup.py install");
system("cd ~/compiz/fusion-icon");
system("make");
system("sudo make install");

return 0;  }
```

---

### Post by CptPicard on 2007-08-24
Is there some particular problem with this program of yours you need help with?

---

### Post by Wybiral on 2007-08-24
You should use the right tool for the right job...

It's mostly shell... Why not use BASH instead of C?

That way your code isn't cluttered with all of those "system" calls.

I don't really see any immediate reason to use C for this.

---

### Post by bjarneh on 2007-08-24
it's possible it's right on, but hard to say, make your girlfriend try it out first on her install, then you'll know :-)

---

### Post by slavik on 2007-08-24
if you want to do something truly not simple, pretend that there is no shell (system() is unavailable) and use fork, exec and wait. :)

---

### Post by AlexenderReez on 2007-08-24
> **Wybiral said:**
> You should use the right tool for the right job...

It's mostly shell... Why not use BASH instead of C?

That way your code isn't cluttered with all of those "system" calls.

I don't really see any immediate reason to use C for this.

i do realized that....i'm learning python...c..perl...bash in parallel..i'm able to wring prefect code in bash for this..as bash is really easy to work with...but i believe can try to code in other language....(at least i don't waste my knowledge)

> **CptPicard said:**
> Is there some particular problem with this program of yours you need help with?

not really....that why i hope anybody can check it.....hm...i will give try by myself....

---

### Post by AlexenderReez on 2007-08-24
> **slavik said:**
> if you want to do something truly not simple, pretend that there is no shell (system() is unavailable) and use fork, exec and wait. :)

i don't really sure how integrate that....any example please....

---

### Post by slavik on 2007-08-24
very simple example (exec and wait calls are wrong, function names are different, check man pages):

//somewhere in main
int fret;

switch (fret = fork()) {
 case -1: /*couldn't fork*/  break;
 case 0: /*new process*/ exec("program","program","param1", NULL); printf("couldn't fork\n"); break;
 default; wait(fret,NULL);
}

---

### Post by AlexenderReez on 2007-08-24
> **slavik said:**
> very simple example (exec and wait calls are wrong, function names are different, check man pages):

//somewhere in main
int fret;

switch (fret = fork()) {
 case -1: /*couldn't fork*/  break;
 case 0: /*new process*/ exec("program","program","param1", NULL); printf("couldn't fork\n"); break;
 default; wait(fret,NULL);
}

interesting ....thanks for idea...

---

### Post by slavik on 2007-08-24
so you know: those are actual calls to the kernel :)

---

### Post by Wybiral on 2007-08-25
> **AlexenderReez said:**
> i do realized that....i'm learning python...c..perl...bash in parallel..i'm able to wring prefect code in bash for this..as bash is really easy to work with...but i believe can try to code in other language....(at least i don't waste my knowledge)

If it's for practice or education then I completely understand, I was just stating that as an actual piece of software, install programs/scripts are better suited to be written in a language like BASH.

But yes, if it's practice, then keep practicing and try to learn to do it more in the C fashion. "system" is a command you'll probably want to avoid in C, but instead try as slavik suggested and use the unix library for it (it's no less portable then using "system").

---

