---
title: "Shell Extensions"
date: 2011-06-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-06-15
How do you get this thing to show themes or shell extensions. works in gNatty but I cant figure it ou t in OO ?

---

### Post by 23dornot23d on 2011-06-15
I have two in the ./local/...... Extensions and the others in a folder in there should I need them

[IMG]http://img15.imageshack.us/img15/1797/screenshot8sq.jpg[/IMG]


The problem can sometimes be related to the version number in the metadata.json

For the two in there at present in my .local/ at the moment it looks like this ....

The 3.0.1 ...... and works on my machine like this ...


{
    "shell-version": ["3.0.1"],
    "uuid": "themeselector@fpmurphy.com",    
    "name": "GNOME Shell Theme Selector",
    "url": "http://fpmurphy.com/themeselector",
    "description": "Enables user to change custom GNOME Shell themes"
}


{
 "uuid": "user-theme@gnome-shell-extensions.gnome.org",
 "name": "User Themes",
 "description": "Load shell themes from user directory",
 "shell-version": [ "3.0.1" ],
 "localedir": "/usr/share/locale",
 "original-authors": [ "john.stowers@gmail.com" ],
 "url": "http://git.gnome.org/gnome-shell-extensions"
}


And one in the usr/share/gnome-shell/extensions/ 

which looks like this ...... ( set like this everything runs ok)

but it does report in looking glass that there are duplicates ....... ( alt + f2 ) lg

[IMG]http://img687.imageshack.us/img687/4587/screenshot16s.jpg[/IMG]



Which at the moment results in this

[IMG]http://img810.imageshack.us/img810/7121/screenshot10vn.jpg[/IMG]


and this .....

[IMG]http://img268.imageshack.us/img268/361/screenshot12sg.jpg[/IMG]


Still working on this .... as I have only just nicely got it all running .... everything works but the version numbers and duplicates may be causing problems for some people.

Even though I am running Gnome 3.0.2
the metadata.json files for the above only work properly set to 3.0.1 ..... as shown above ..... for me.

---

### Post by Quackers on 2011-06-15
Here's mine

---

### Post by 23dornot23d on 2011-06-15
Cheers Quackers .... 

I have a feeling everybody that has it running in here may have similar results.
( but if anybody does have them working ok in 11.10 - please post the contents of the extensions folders and the metadata.json files (please) to show others how ..... you have them set up )

Until that time though .....

If you [**go to my page**]("http://ubuntuforums.org/member.php?u=953253") I have created a download ..... its 3.8 Gig in size
but its got the latest 11.10 kernel  3.0.0  ..... the Nvidia Drivers for 275.09.04 ...... and is set up
so that the Themes Work and you can swap from Compiz to Gnome-shell and back etc.

Its a Demo Dvd and only meant as a means of showing how it will run ..... on 11.10.
Works for Nvidia only at this moment in time .... as I do not have any other graphics
cards other than Nvidia to test it out on ......

---

