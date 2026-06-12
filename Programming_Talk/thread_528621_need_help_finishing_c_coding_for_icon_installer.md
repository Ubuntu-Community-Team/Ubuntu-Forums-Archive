---
title: "need help finishing c coding for icon installer"
date: 2007-08-18
forum: Programming Talk
---

### Post by AlexenderReez on 2007-08-18
hi there...

i'm trying to install icons theme that i remodified using c code....this is the code

for install.c

> //modification icon by alexender reez(amirulraz@gmail.com)

#include <stdio.h>
#include <string.h>

main() {
int choice=0, color=0;
char def[2000];           //determine buffer overflow
char user[2000];
char home[] = "/home/";        // home folder
FILE *username;

def[0]='@';
def[1]='@';

system ("whoami > /tmp/.user");    //find user in /tmp/.user 
username = fopen ("/tmp/.user", "rb");
fscanf (username, "%s", user);          //check user privillege 
strcat (home, user);
fclose (username);
system ("rm /tmp/.user"); 
strcat (home, "/.nicole");

printf ("\nWelcome to nicole installation wizard!");
printf ("\nThis icon theme is for both Gnome and KDE.");
printf ("\nMimelnk/services/apps are only for KDE.");
printf ("\nDefault choice is to install the icon theme and the mimelnk/services/apps.");

while (def[0]!='y' && def[0]!='n' || def[1]!='\0')   {               //do user want default process?
printf ("\nD'you wanna proceed with the default choice? (y/n) ");
scanf ("%s", def);    
if (def[0]!='y' && def[0]!='n' || def[1]!='\0')   {  
printf("\nERROR: choice not valid!\n");             } } 

if (def[0]=='y') {                                            //if default
choice=1;       color=2; 
goto start;
}

printf("\nWhat d'you wanna do?\n");
printf("1) Install/upgrade nicole  icons;\n");
printf("2) Uninstall nicole ;\n");
printf("3) Save your mimetypes;\n");
printf("4) Exit\n\n");

while (choice != 1 && choice !=2 && choice!=3 && choice!=4) {         //other options
printf("Enter your choice: ");
scanf ("%d", &choice);
if (choice!=1 && choice!=2 && choice!=3 && choice!=4) printf("\nERROR: choice not valid!\n");

}

if (choice==1) {          //install icon:)

fputs("\nCreating nicole directories.............................. ", stderr);
system("rm -r -f ~/.kde/share/icons/nicole");
system("rm -r -f ~/.icons/nicole");
system("mkdir -p ~/.kde/share/icons/nicole");
system("mkdir -p ~/.icons/nicole");
printf("done\n");
fputs ("Copying icons......................................................... ", stderr);
system("cp -r scalable ~/.kde/share/icons/nicole/");
system("cp -r scalable ~/.icons/nicole/");
printf("done\n");

fputs ("Copying theme index................................................... ", stderr);
system("cp ./hidden/index.txt ~/.kde/share/icons/nicole/index.theme");
system("cp ./hidden/index.txt ~/.icons/nicole/index.theme");
printf("done\n");
printf("\nOperation successfully completed.\n");
return 0;
	}

if (choice==2) {                      //remove icon

if ((fopen (home, "rb"))==0) {
	printf ("\nTheme is not installed: nothing to be done.\n");
	return 0;
	}

system ("rm -r -f ~/.nicole");
fputs ("\nRemoving theme........................................................ ", stderr);
system ("rm -r -f ~/.kde/share/icons/nicole");
system ("rm -r -f ~/.icons/nicole");

system ("rm -r -f ~/.kde/share/mimelnk/*");    
system ("cp -r ./backup/mimelnk ~/.kde/share/");  

system ("rm -r -f ~/.local/share/applications/*");
system ("cp -r ./backup/applications ~/.local/share/");

system ("rm -r -f ~/.kde/share/services/*"); 
system ("cp -r ./backup/services ~/.kde/share/");

printf("done\n");
printf("\nOperation successfully completed.\n");
return 0;
} 

if (choice == 3) {               //Save mimetypes

fputs ("\nSaving applications folder............................ ", stderr);
system ("mkdir -p ~/.local/share/applications");
system ("cp -r ~/.local/share/applications ./hidden/");
printf ("done\n");

fputs ("Saving mimelnk folder................................. ", stderr);
system ("mkdir -p ~/.kde/share/mimelnk");
system ("cp -r ~/.kde/share/mimelnk ./hidden/");
printf ("done\n");

fputs ("Saving services folder................................ ", stderr);
system ("mkdir -p ~/.kde/share/services");
system ("cp -r ~/.kde/share/services ./hidden/");
printf ("done\n");

printf("\nOperation successfully completed.\n");
return 0;
}

if (choice==4) return 0;           //exit

//reaL installation

start:
          
if ((fopen (home, "rb"))!=0) { 
	
fputs ("\nSaving applications folder............................ ", stderr);
system ("mkdir -p ~/.local/share/applications");
system ("cp -r ~/.local/share/applications ./hidden/");
printf ("done\n");

fputs ("Saving mimelnk folder................................. ", stderr);
system ("mkdir -p ~/.kde/share/mimelnk");
system ("cp -r ~/.kde/share/mimelnk ./hidden/");
printf ("done\n");

fputs ("Saving services folder................................ ", stderr);
system ("mkdir -p ~/.kde/share/services");
system ("cp -r ~/.kde/share/services ./hidden/");
printf ("done\n");    }

else {
system ("mkdir -p ~/.kde/share/services");          //create icon backup 
system ("mkdir -p ~/.kde/share/mimelnk");
system ("mkdir -p ~/.local/share/applications");
system ("rm -r -f ./backup/*");
system ("mkdir ./backup/services");
system ("mkdir ./backup/mimelnk");
system ("mkdir ./backup/applications");
system ("cp -r ~/.kde/share/services ./backup/");
system ("cp -r ~/.kde/share/mimelnk ./backup/");
system ("cp -r ~/.local/share/applications ./backup/");
	}

system ("touch ~/.nicole");

fputs ("\nCreating nicole directories.............................. ", stderr);
system("rm -r -f ~/.kde/share/icons/nicole");
system("rm -r -f ~/.icons/nicole");
system("mkdir -p ~/.kde/share/icons/nicole");
system("mkdir -p ~/.icons/nicole");
printf("done\n");
fputs ("Copying icons......................................................... ", stderr);
system("cp -r scalable ~/.kde/share/icons/nicole/");
system("cp -r scalable ~/.icons/nicole/");
printf("done\n");

fputs ("Copying theme index................................................... ", stderr);
system("cp ./hidden/index.txt ~/.kde/share/icons/nicole/index.theme");
system("cp ./hidden/index.txt ~/.icons/nicole/index.theme");
printf("done\n");

fputs ("Installing mimelnk folder............................................. ", stderr);
system ("mkdir -p ~/.kde/share/mimelnk/");
system("cp -r ./hidden/mimelnk ~/.kde/share/");
printf("done\n");

fputs ("Installing services folder............................................ ", stderr);
system ("mkdir -p ~/.kde/share/services/");
system("cp -r ./hidden/services ~/.kde/share/");
printf("done\n");

fputs ("Installing applications folder........................................ ", stderr);
system ("mkdir -p ~/.local/share/applications/");
system("cp -r ./hidden/applications ~/.local/share/");
printf("done\n");

printf("\nOperation successfully completed.\n");

return 0;  }


and for** makefile**

> 
all: clean compile

compile:
	gcc -o install install.c
	
clean:
	rm -r -f install


it is seems succeed for first time only...any idea why?

second time give this -->

> reez@aLeXeNdeRreEz:~/Desktop/Works/nicloe$ make
rm -r -f install
gcc -o install install.c
reez@aLeXeNdeRreEz:~/Desktop/Works/nicloe$ sudo make install
[sudo] password for reez:
make: `install' is up to date.
reez@aLeXeNdeRreEz:~/Desktop/Works/nicloe$ 

---

### Post by AlexenderReez on 2007-08-18
nevermind..already succeed :)

---

### Post by moma on 2007-08-18
A tip:

Programs should use **Xdg-utils** to install new icons and menu items. 
See: [http://portland.freedesktop.org/wiki/](http://portland.freedesktop.org/wiki/)

Xdg is desktop-independent. It works regardless you run GNOME, KDE (or XFCE).

---

