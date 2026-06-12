---
title: "first panecake"
date: 2011-12-23
forum: Programming Talk
---

### Post by Jacobonbuntu on 2011-12-23
Hi people,

if someone would look at the following (Python) script and run it, I would much appreciate your comment. As a complete illiterate, I just started learning Python a (very, very little) bit. looked through the "non-programmers tutorial", and having a lot of fun with it.

I made this script that automatically generates the complete code for a custom nautilus-home.desktop file (Unity). It asks the user a few simple questions to do so.
As I will (hopefully) improve my knowledge, I will make the script actually edit the .desktop file, add the possibility to create dividers, and I hope to be able to make a gui for it.

I don't know if the script is displayed correctly so I will add it separately...

[PHP]#just picked up python by reading the "non-programmers tutorial", and
#think it is a lot of fun :)
#the goal of this script is to automatically generate te (complete) code
#for a custom home launcher, as a replacement for the standard home launcher
#the user is asked a few questions on which the generated code is made
#my goal is, eventually, to make a link in the home launcher to easily edit
#its entries

countdividers = 0
approval = raw_input("This script will ask you a few (necessary) questions\nto make a custom home-launcher.\n\nWould you like to continue? type y/n ")
if approval == "y":
    entrylist = "X-Ayatana-Desktop-Shortcuts="
    entries = ""
    user = raw_input("\nok, here we go; what is your user name? ")
    while approval != "n":
        categorie = raw_input("would you like to add a directory or a divider? type dir/div ")
        if categorie == "dir":
            adddir = raw_input("what is the directory you want to add? ")
            name = raw_input("what directory-name do you want to appear in the list? ")
            entrylist = entrylist+name+";"
            adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus"+" "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
            print "done..."
            approval = raw_input("\nwould you like to add more? type y/n ")
            entries = entries+adddirentry
        else:
            #hier moet komen wat er gebeurt als er een divider wordt toegevoegd
            countdividers = countdividers + 1
            if countdividers == 1:
                name = "divider 1"
            elif countdividers == 2:
                name = "divider 2"
            elif countdividers == 3:
                name = "divider 3"
            elif countdividers == 4:
                name = "divider 4"
            elif countdividers == 5:
                name = "divider 5"
            elif countdividers == 6:
                name = "divider 6"
            elif countdividers == 7:
                name = "divider 7"
            entrylist = entrylist+name+";"
            adddirentry = "["+name+" Shortcut Group]\n""Name=-----------------------------\n""Exec=\n""OnlyShowIn=Unity\n\n"
            print "done..."
            approval = raw_input("\nwould you like to add more? type y/n ")
            entries = entries+adddirentry
            
                
    print "\n\n==================================\ncopy the code below:\n"
    print "[Desktop Entry]\nName=Home Folder\nGenericName=Home Folder\nX-GNOME-FullName=Home Folder\nComment=Open your favourite folders in Nautilus\nExec=nautilus /home/"+user+"\nIcon=user-home\nTerminal=false\nType=Application\nCategories=GNOME;GTK;Core;\nStartupNotify=true\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Product=nautilus\nX-GNOME-Bugzilla-Component=general\nX-Ubuntu-Gettext-Domain=nautilus\n"
    print entrylist+ "\n\n"
    print entries
else:
    print "ok, we'll quit then" 
[/PHP]

edit... made an improved version, still having fun

---

