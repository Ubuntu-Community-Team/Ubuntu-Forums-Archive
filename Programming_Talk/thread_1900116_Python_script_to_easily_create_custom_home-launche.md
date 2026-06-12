---
title: "Python script to easily create custom home-launcher for Unity"
date: 2011-12-25
forum: Programming Talk
---

### Post by Jacobonbuntu on 2011-12-25
I made a Python script to easily create a home launcher with a quick list for directories. everyone who  understands what a directory is should be able to use the script without  any knowledge of .desktop files.

I appologize for posting again on the same subject, but the title of the first one was not only unclear, but also misspelled. Also the script was in a very early stage, and only worked on Dutch systems (I used "Bureaublad" instead of Desktop in directories). I would appreciate someone to remove the first post (titled "panecake :()

here is what the scrypt does:
- ask the user what directories should be included
- ask whether dividers should be used between directory names
- let the user preview the launcher and / or the code
- create the path to the nautilus-home.desktop file (if necessary; /home/user/.local/share/applications)
- edit the .desktop file, or create it if it is not there

in the script I attached, I let it create the file on the desktop instead of in ~/.local/share/applications, to prevent overwriting your existing .desktop-file for now. The file should work fine though.

I am very well aware that it is not a polished thing yet: I just starting to look into Python a few weeks ago, actually into coding whatsoever at all. 
Therefore I would really appreciate any comment and/or tips, no matter what.

[PHP]#!/usr/bin/python
#setting global variables:

#entrylist: the (growing)list of entries to appear in the launcher (in the same order)
#entries: the (growing) list of shortcuts and their execute-commands
#countdividers: counts the dividers in order to automatically them different
#names in the entrylist
#countentries: the only reason to count the entries is to prefend the user to be asked
#twice if he or she wants to continue at the beginning of the program;
#therefor option [3] (finish) is blocked the first time
#preview: after finishing, a preview is presented before the code is written
#to the nautilus-home.desktop file
#user: the username, needed to create entries and save the code

entrylist = "X-Ayatana-Desktop-Shortcuts="
entries = ""
countdividers = 0
countentries = 0
preview = ""
user = ""

#explains what the program does and asking if the user wants to continue:
#(if not we jump to the last line)

approval = raw_input("This script will ask you a few (necessary) questions\nto make a custom home-launcher.\n\nWould you like to continue? type y/n ")
if approval == "y":
    user = raw_input("\nok, here we go; what is your user name? ")
    
    #in this whole while- section the user gives his input to generate the code 
    while approval != "n":
        countentries = countentries + 1
        #in this first loop cyclus, the option [3] (finish) is not available, because
        #the user is justed asked if he wants to continue :)
        if countentries < 2:
            categorie = raw_input("\nwhat would you like to do?\n[1]= add a directory [2]= add a divider ")

            #asks for the directory, its name in the launcher, adds it to the list
            if categorie == "1":
                adddir = raw_input("\nwhat is the directory you want to add? ")
                name = raw_input("what directory-name do you want to appear in the list? ")
                entrylist = entrylist+name+";"
                preview = preview+name+"\n"
                adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
                print "\ndone..."
                entries = entries+adddirentry

            #adds a divider, generates its name
            elif categorie == "2":
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
                elif countdividers == 8:
                    name = "divider 8"
                elif countdividers == 9:
                    name = "divider 9"
                elif countdividers == 10:
                    name = "divider 10"
                entrylist = entrylist+name+";"
                preview = preview+"---------------"+"\n"
                adddirentry = "["+name+" Shortcut Group]\n""Name=-----------------------------\n""Exec=\n""OnlyShowIn=Unity\n\n"
                print "\ndone..."
                entries = entries+adddirentry

        #in the second (and so on) loop cyclus, the user has the option to finish;
        #option [3]
        else:
            categorie = raw_input("\nwhat would you like to do?\n[1]= add a directory [2]= add a divider [3]=finish ")

            #asks for the directory, its name in the launcher, adds it to the list
            if categorie == "1":
                adddir = raw_input("\nwhat is the directory you want to add? ")
                name = raw_input("what directory-name do you want to appear in the list? ")
                entrylist = entrylist+name+";"
                preview = preview+name+"\n"
                adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus"+" "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
                print "\ndone..."
                entries = entries+adddirentry

            #adds a divider, generates its name
            elif categorie == "2":
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
                elif countdividers == 8:
                    name = "divider 8"
                elif countdividers == 9:
                    name = "divider 9"
                elif countdividers == 10:
                    name = "divider 10"
                entrylist = entrylist+name+";"
                preview = preview+"---------------"+"\n"
                adddirentry = "["+name+" Shortcut Group]\n""Name=-----------------------------\n""Exec=\n""OnlyShowIn=Unity\n\n"
                print "\ndone..."
                entries = entries+adddirentry

            #terminates the loop when option [3] is chosen 
            elif categorie == "3":
                approval = "n"
            
    #a preview of the list, as it will appear in the launcher
    print "\n\n==================================\nhere is a preview of the launcher that will be created:\n"
    print preview
    print "\n\n=================================="

    #under construction....
    viewcode = raw_input ("\nwould you like to preview the code before proceeding?\n[1]=preview code [2]=finish procedure [3]=abbort procedure ")
    if viewcode == "1":
        #a preview of the code that will replace the existing code        
        print "\n\n==================================\na preview of the code that will replace the existing code\nof the .desktop -file:\n"
        print "[Desktop Entry]\nName=Home Folder\nGenericName=Home Folder\nX-GNOME-FullName=Home Folder\nComment=Open your favourite folders in Nautilus\nExec=nautilus /home/"+user+"\nIcon=user-home\nTerminal=false\nType=Application\nCategories=GNOME;GTK;Core;\nStartupNotify=true\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Product=nautilus\nX-GNOME-Bugzilla-Component=general\nX-Ubuntu-Gettext-Domain=nautilus\n"
        print entrylist+ "\n\n"
        print entries
        
        applychanges = raw_input ("\nwould you like to apply the changes or abbort?\n[1]=apply changes [2]=abbort procedure ")
        if applychanges == "1":
            #creates path(if it is not there) opens the document
            #(creates it if it is not there) and writes the code into it
            import os
            if not os.path.exists("/home/"+user+"/Desktop/share/applications"):
                os.makedirs("/home/"+user+"/Desktop/share/applications")
            f = open("/home/"+user+"/Desktop/share/applications/nautilus-home.desktop","w")
            #the code below is replacing the contents of the file in the directory above
            print >>f,"[Desktop Entry]\nName=Home Folder\nGenericName=Home Folder\nX-GNOME-FullName=Home Folder\nComment=Open your favourite folders in Nautilus\nExec=nautilus /home/"+user+"\nIcon=user-home\nTerminal=false\nType=Application\nCategories=GNOME;GTK;Core;\nStartupNotify=true\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Product=nautilus\nX-GNOME-Bugzilla-Component=general\nX-Ubuntu-Gettext-Domain=nautilus\n"
            print >>f, entrylist+ "\n\n"
            print >>f, entries
            print "ok, done. after you close this window, your launcher will be created!"
        else:
            print "ok, we'll quit, your launcher will not be changed, you can clos this window."
            
        
    elif viewcode == "2":
        #creates path(if it is not there) opens the document
        #(creates it if it is not there) and writes the code into it
        import os
        if not os.path.exists("/home/"+user+"/Desktop/share/applications"):
            os.makedirs("/home/"+user+"/Desktop/share/applications")
        f = open("/home/"+user+"/Desktop/share/applications/nautilus-home.desktop","w")
        #the code below is replacing the contents of the file in the directory above
        print >>f,"[Desktop Entry]\nName=Home Folder\nGenericName=Home Folder\nX-GNOME-FullName=Home Folder\nComment=Open your favourite folders in Nautilus\nExec=nautilus /home/"+user+"\nIcon=user-home\nTerminal=false\nType=Application\nCategories=GNOME;GTK;Core;\nStartupNotify=true\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Product=nautilus\nX-GNOME-Bugzilla-Component=general\nX-Ubuntu-Gettext-Domain=nautilus\n"
        print >>f, entrylist+ "\n\n"
        print >>f, entries
        print "ok, done. after you close this window, your launcher will be created!"

    elif viewcode == "3":
        print "ok, we'll quit, your launcher will not be changed, you can clos this window."
        
    
#if the user wants to quit, right from the start:
else:
    print "ok, we'll quit then"





    [/PHP]

---

### Post by moephan on 2011-12-28
Hi Jacobonbuntu,

It's a nice script. Could I suggest that you push it to launchpad? That way, it will be very easy for people to collaborate on it with you.

Cheers, Rick

---

### Post by Jacobonbuntu on 2011-12-28
> **moephan said:**
> Hi Jacobonbuntu,

It's a nice script. Could I suggest that you push it to launchpad? That way, it will be very easy for people to collaborate on it with you.

Cheers, Rick

Thanks a lot!!
I will push it to launchpad; it's new to me, but I'll find out how it works
meanwhile I worked a little further on it, actually kind of remade it:

- added the option to create a directory on the fly and add it to the quick-list at the same time if the directory not exists (yet). might be useful to quickly organize directories after a fresh install
- I added a lot of "safety precautions" to prevent users from making mistakes, like forgetting to start with "/" or using spaces in names.
- forcing the user to give a (required) answer if "y" or "n" is required

I tried it out a lot with very different inputs and it works perfectly and fast. 
I have one question: some code I had to repeat a few times (I marked it) could that be handled in one "module" or something?
for example line 82-94...

this is the code:
[PHP]
#!/usr/bin/env python
import os
########################################################################
# setting global variables:

# entrylist: the (growing)list of entries to appear in the launcher
# (in the same order)

# entries: the (growing) list of shortcuts and their execute-commands

# countdividers: counts the dividers in order to automatically give
# every divider a unique name in the entrylist

# go_on makes the script return to the beginning of the loop after
# abbortion the creation of a non-existan directory

# preview: after finishing, a preview is presented before the code is
# written to the nautilus-home.desktop file

# user: the username, needed to create entries and save the code

entrylist = "X-Ayatana-Desktop-Shortcuts="
entries = ""
countdividers = 0
go_on = "y"
preview = ""
user = ""

########################################################################
# introduction:
# options to the user: > continue / > abbort

approval = raw_input ("\n\nThis script will ask you a few (necessary) questions to make a\ncustom home-launcher with a quicklist of directories.\n\nWould you like to continue? type y/n ")
while approval != "y" and approval != "n":
    if approval == "Y" or approval == "N":
        approval = raw_input ("Caps Lock is on, please try again: ")
    else:
        approval = raw_input ("please type y or n: ")
        
# [this section is ok]
########################################################################
# start of the actual script to generate the code:

if approval == "y":
    user = raw_input("\nok, here we go; what is your user name? ")
    
# [this section is ok]
#-----------------------------------------------------------------------

while go_on == "y":
    categorie = raw_input("\nwhat would you like to do?\n[1]= add a directory [2]= add a divider [3]=finish ")
    while categorie != "1" and categorie != "2" and categorie != "3":
        categorie = raw_input ("please choose [1]= add a directory [2]= add a divider [3]=finish: ")
    if categorie == "3":
        go_on = "n"
    
    # remember: do not print entries if entries = "" due to option [3]!!
    
# [this section is ok]   
#-----------------------------------------------------------------------
# executing option [1]; creating an entry and a directory (if necessary)

    elif categorie == "1":
        # make input idiot-proof: checking for spaces, "/" at the start and
        # if the directory exists. asks for permission to creat it if not...
        adddir = raw_input("what is the directory you want to add? ")
        string = adddir;
        if(string[0]) != ("/") or adddir.count(" ") != 0 or not os.path.exists(adddir):
            while(string[0]) != ("/") or adddir.count(" ") != 0:
                print "your directory should begin with a slash / and should not include\nnames with spaces..."
                adddir = raw_input("please try again; what is the directory you want to add? ")
                string = adddir;
            if not os.path.exists(adddir):
                create_it = raw_input("the directory name seems ok, but does not exist on\nyour system. Should I create it? y/n ")
                while create_it != "y" and create_it != "n":
                    if create_it == "Y" or create_it == "N":
                        create_it = raw_input ("Caps Lock is on, please try again: ")
                    else:
                        create_it = raw_input ("please type y or n: ")
                if create_it == "y":
                    os.makedirs(adddir)
                    ##########################################################################
                    # ask for the desired name in the launcher, adds it to the list 
                    # >>>>>> find out if this can be coded more efficient, in one module or something...
                    # ....so I won't have to reapeat it in several occuring occasions
                    name = raw_input("what directory-name do you want to appear in the list? ")
                    entrylist = entrylist+name+";"
                    preview = preview+name+"\n"
                    adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
                    print "\ndone..."
                    entries = entries+adddirentry
                    #---------------
                    print "preview:\n=========================\n\n"+preview+"\n\n========================="
                    ##########################################################################
                elif create_it == "n":
                    print "ok, the directory will not be created\n"
                    go_on = raw_input("would you like to continue? type y/n " )
                    while go_on != "y" and go_on != "n":
                        if go_on == "Y" or go_on == "N":
                            go_on = raw_input ("Caps Lock is on, please try again: ")
                        else:
                            go_on = raw_input ("please type y or n: ")           
            else:
                ##########################################################################
                # ask for the desired name in the launcher, adds it to the list 
                # >>>>>> find out if this can be coded more efficient, in one module or something...
                # ....so I won't have to reapeat it in several occuring occasions
                name = raw_input("what directory-name do you want to appear in the list? ")
                entrylist = entrylist+name+";"
                preview = preview+name+"\n"
                adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
                print "\ndone..."
                entries = entries+adddirentry
                #---------------
                print "preview:\n=========================\n\n"+preview+"\n\n========================="
                ##########################################################################
        else:
            ##########################################################################
            # ask for the desired name in the launcher, adds it to the list 
            # >>>>>> find out if this can be coded more efficient, in one module or something...
            # ....so I won't have to reapeat it in several occuring occasions
            name = raw_input("what directory-name do you want to appear in the list? ")
            entrylist = entrylist+name+";"
            preview = preview+name+"\n"
            adddirentry ="["+name+" Shortcut Group]\n""Name="+name+"\n""Exec=nautilus "+adddir+"\n"+"OnlyShowIn=Unity\n\n"
            print "\ndone..."
            entries = entries+adddirentry
            #---------------
            print "preview:\n=========================\n\n"+preview+"\n\n========================="
            ##########################################################################

# [this section is ok]   
#-----------------------------------------------------------------------
# executing option [2]; creating a divider
#adds a divider, generates its name


    elif categorie == "2":
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
        elif countdividers == 8:
            name = "divider 8"
        elif countdividers == 9:
            name = "divider 9"
        elif countdividers == 10:
            name = "divider 10"
        entrylist = entrylist+name+";"
        preview = preview+"---------------"+"\n"
        adddirentry = "["+name+" Shortcut Group]\n""Name=-----------------------------\n""Exec=\n""OnlyShowIn=Unity\n\n"
        print "\ndone..."
        entries = entries+adddirentry
        print "preview:\n=========================\n\n"+preview+"\n\n========================="

# [this section is ok]   
#-----------------------------------------------------------------------
# executing option [3]; finishing
# options to the user: > apply changes, previewing the code /
# apply without previewing the code / > cancel all changes




            
if go_on == "n" and entries != "":
    save_code = raw_input("would you like to save the launcher? y/n ")
    while save_code != "y" and save_code != "n":
        if save_code == "Y" or save_code == "N":
            save_code = raw_input ("Caps Lock is on, please try again: ")
        else:
            save_code = raw_input ("please type y or n: ")
            #creating final preview if creation is approved
    if save_code == "y":
        print "\n\n=========================\nhere is a the final preview of the launcher that will be created:\n========================="
        print preview+"\n\n========================="
        ######################################################################
        #productie code en wegschrijven toevoegen
        ######################################################################
        
        #the changes will be applied
        applychanges = raw_input ("\nwould you like to apply the changes? y/n ")

        while applychanges != "y" and applychanges != "n":
                        if applychanges == "Y" or applychanges == "N":
                            applychanges = raw_input ("Caps Lock is on, please try again: ")
                        else:
                            applychanges = raw_input ("please type y or n: ")

                            
        if applychanges == "y":
            #creates path(if it is not there) opens the document
            #(creates it if it is not there) and writes the code into it
            if not os.path.exists("/home/"+user+"/.local/share/applications"):
                os.makedirs("/home/"+user+"/.local/share/applications")
            f = open("/home/"+user+"/.local/share/applications/nautilus-home.desktop","w")
            #the code below is replacing the contents of the file in the directory above
            print >>f,"[Desktop Entry]\nName=Home Folder\nGenericName=Home Folder\nX-GNOME-FullName=Home Folder\nComment=Open your favourite folders in Nautilus\nExec=nautilus /home/"+user+"\nIcon=user-home\nTerminal=false\nType=Application\nCategories=GNOME;GTK;Core;\nStartupNotify=true\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Product=nautilus\nX-GNOME-Bugzilla-Component=general\nX-Ubuntu-Gettext-Domain=nautilus\n"
            print >>f, entrylist+ "\n\n"
            print >>f, entries
            print "ok, done. after you close this window, your launcher will be created!"
        else:
            print "ok, we'll quit, your launcher will not be changed, you can clos this window."


        
# [this section is uc, want to add the possibility to preview the code (again)]        
##########################################################################
[/PHP]to run it, open a terminal, cd to directory and use the command "python versie2a.py"

edit: one more version on this , directory-names with spaces are allowed now in "versie2b.py" :)
edit 2: I pushed it to launchpad, [here]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/files")

---

