---
title: "Would it useful to temporarily change permissions by right clicking?"
date: 2006-12-08
forum: Programming Talk
---

### Post by Hendrixski on 2006-12-08
Would it be a useful feature for you to be able to change the permissions on a file or folder by right clicking and choosing a "change permissions" option, then an application pops up, that changes the permissions, with the option of restoring them to their defaults after you close the application?

I put this in programming talk because I think this may be a fun project for me over Christmas holidays.  And while I have worked with open source Java libraries for customers, I have never modified them and posted them back to source yet.  So I'd like to know where to start.  Oh, and which project I would be contributing to (GNOME?).

---

### Post by Choad on 2006-12-08
right click->properties 

??

in thunar at least... i think gnome is the same

---

### Post by Wybiral on 2006-12-08
Same here, I have edgy and I previously had dapper, and in both I could change permissions by: rightclick->properties->permission tab.

Also, I don't mind using the command line for stuff like that, you can enable an entire folder's worth of files to execute just by typing "chmod a=x *" which is alot faster than right clicking all of them!

---

### Post by Mickeysofine1972 on 2006-12-08
Dunno if it me but shouldn't it really give you  the choice anyway?

This is just one of those thing you 'expect' the OS to do isn't it?

maybe I'm wrong but wouldn't that be nice!


Mike

---

### Post by bradleyd on 2006-12-08
gnome and kde have permission on rigth click.(as long as I can remeber) If you really want todo something different, you can write an app that you can open file selection and choose file to add or takeaway permissions from, then you could add it gnome-panel for easy access. I use something similar when I am writing scripts.

---

### Post by rfruth on 2006-12-08
I already get myself in enough trouble, make it easier - I voted NO

---

### Post by Wybiral on 2006-12-08
How about this for a panel script, it uses zenity for the dialog.

```

#!/bin/bash

infile=`zenity  --title="Select a file chmod" --file-selection`
access=`zenity --title  "chmod" --entry --text "Please enter the access mode (example: a=rw)"`

echo "chmod -c $access $infile"
chmod -c $access $infile

zenity --text="chmod complete!" --info

```

---

### Post by bradleyd on 2006-12-08
interesting, here is on with perl/Tk

#!/usr/bin/perl -w

use Tk 804;
use Shell;
#
# Global variables
#
my (
     # MainWindow
     $MW,

     # Hash of all widgets
     %ZWIDGETS,
    );

#
# User-defined variables (if any)
#

######################
#
# Create the MainWindow
#
######################

$MW = MainWindow->new;

######################
#
# Load any images and fonts
#
######################
ZloadImages();
ZloadFonts ();
my $icon = $MW-> Photo(-file => '/home/someicon.gif');
$MW->idletasks;
$MW-> iconimage($icon);

$MW -> bind('<Key-Escape>', sub { exit });

# Widget Label1 isa Label
$ZWIDGETS{'Label1'} = $MW->Label(
   -font    => '_12_bold_roman_',
   -justify => 'center',
   -text    => 'Chmod',
  )->grid(
   -row    => 0,
   -column => 0,
  );
# Widget Label2 isa Label
$ZWIDGETS{'Label2'} = $MW->Label(-textvariable=>\$message,
   -text => 'Label2',
  )->grid(
   -row    => 1,
   -column => 0,
  );
# Widget Entry1 isa Entry
my $entry1 = $MW->Entry(-width => 30)->grid(
   -row    => 2,
   -column => 0,
  );

# Widget Button2 isa Button
$ZWIDGETS{'Button2'} = $MW->Button(-command=>\&select_file,
   -text => 'Search',
  )->grid(
   -row    => 1,
   -column => 1,
  );

# Widget Button1 isa Button
$ZWIDGETS{'Button1'} = $MW->Button(-command=>\&change_perm,
   -text => 'Change',
  )->grid(
   -row    => 2,
   -column => 1,
  );

###############
#
# MainLoop
#
###############
my $types = [ ['All Files',   '*'],];
MainLoop;

#######################
#
# Subroutines
#
#######################



sub change_perm {
	
	my $value = $entry1->get();
	chomp $value;
	my @result = `chmod u+x $value 2>&1`;
	
	if (@result gt 0) {
       	$MW->messageBox(-message=>@result,-title=>"OOPS!",-icon=>'error');
}else{
	$message = "Permissions Changed";
	
   }
}
sub select_file {
	my $open = $MW->getOpenFile(-filetypes => $types,
                              -defaultextension => '.pl');
	$entry1->delete(0,'end');
	$entry1->insert(0,"$open");
}
sub ZloadImages {
}

sub ZloadFonts {
  $MW->fontCreate('_12_bold_roman_',
   -weight     => 'bold',
   -underline  => 0,
   -family     => 'fixed',
   -slant      => 'roman',
   -size       => -15,
   -overstrike => 0,
  );
}

---

### Post by Hendrixski on 2006-12-08
Oh, it's in properties... lol.  I had some friends looking for it, and couldn't find it... I always do stuff from the command line.

Cool, I guess this thread is closed. :)

---

