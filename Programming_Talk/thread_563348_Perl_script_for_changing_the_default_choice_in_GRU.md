---
title: "Perl script for changing the default choice in GRUB"
date: 2007-09-29
forum: Programming Talk
---

### Post by eph1973 on 2007-09-29
I've seen that a lot of newer people ask the question on how to change their default OS on the GRUB menu.  So I thought it might be a good idea to write a quick Perl script to make it easy for them.  I'd like to see what you guys think:  is this going to help anybody, or did I just waste my time, or what.  Feedback is appreciated.

```

#!/usr/bin/perl -w

# The purpose of this script is to allow newer users who wish to change the default OS they boot
# into from the GRUB menu.  It also allows them to change the amount of time before the timeout
# automatically makes the default selection.  I did not give functionality to the other things
# as I figure if you are savvy enough to know what they are for in menu.lst, you don't need a
# script to do it for you.

use strict;

my @operating_systems;
my $menu_number;
my $menu_choice;
my $default_os;
my $grub_index_num = -1;    # the total number of choices in the GRUB menu (including 'Other Operating Systems:', etc.)
my $ORIG_MENU_LST = "/boot/grub/menu.lst";
my $TEMP_MENU_LST = "/boot/grub/menu.tmp";
my $BACKUP_FILE = "/boot/grub/menu.lst.bak";
my %menu_hash;              # hash that keeps track of which place on the menu each menu choice is at
my $orig_timeout;
my $new_timeout;

open MENU_LST, $ORIG_MENU_LST or die "Could not open $ORIG_MENU_LST: $!\n";
open TEMP_MENU, "> $TEMP_MENU_LST" or die "Could not open temporary file: $!\nPlease run this script with the command 'sudo'\n";
open BACKUP, "> $BACKUP_FILE" or die "Could not create backup file: $!\n";

while(<MENU_LST>){
  print BACKUP "$_";
  chomp;
  if(/^\s*title\s*/i){
    $grub_index_num++;
    push(@operating_systems, "$'") if !(/:|memtest|recovery mode/);
    $menu_hash{"$'"} = $grub_index_num;
  } elsif (/^\s*timeout\s*/i){
    $orig_timeout = "$'";
    chomp $orig_timeout;
  }
}
close BACKUP;
close MENU_LST;
open MENU_LST, $ORIG_MENU_LST or die "Could not open $ORIG_MENU_LST: $!";
printf "%s) $_\n", ++$menu_number for @operating_systems;
print "Please enter which OS you would like to be the default OS: ";
$menu_choice = <STDIN>;
chomp $menu_choice;
if($menu_choice <= 0 || $menu_choice > $menu_number || $menu_choice =~ /\D/){
  close MENU_LST;
  close TEMP_MENU;
  close BACKUP;
  unlink $TEMP_MENU_LST or warn "Could not delete temporary file $TEMP_MENU_LST: $!\n";
  die "Invalid menu selection.  Exiting the program to prevent errors from occuring.\nPlease restart the program if you still wish to change your GRUB menu.\n";
}
$menu_choice -= 1;
$default_os = $operating_systems[$menu_choice];
print "Your current timeout before GRUB chooses your default selection is $orig_timeout seconds.\nIf you like this time, just press <Enter>\nIf you would like to change it, enter a new number of seconds GRUB should wait\n: ";
$new_timeout = <STDIN>;
chomp $new_timeout;
if($new_timeout =~ /\d+/){                        # I use $orig_timeout to make the replacements in the while loop below, this checks
  $orig_timeout = $& if ($& > 0 && $& < 30000);   # for valid input to $new_timeout before replacing the value of $orig_timeout 
} else {
  print "Invalid entry, continuing to use $orig_timeout seconds as the default timeout\n";
}
print "\nYour new default will be $default_os\n";
print "Your default timeout will be $orig_timeout\n";
print "Press enter to continue or q to abort\n";
my $abort = <STDIN>;
chomp $abort;
if($abort eq 'q' || $abort eq 'Q'){
  close MENU_LST;
  close TEMP_MENU;
  unlink $TEMP_MENU_LST or warn "Could not delete temporary file $TEMP_MENU_LST: $!\n";
  die "\nAborting.  No changes have been made to $ORIG_MENU_LST\n";
}
while(<MENU_LST>){
  my $menu_line = $_;
  if($menu_line =~ /^\s*default/){
    $menu_line =~ s/\d+/$menu_hash{$default_os}/;
    print TEMP_MENU $menu_line;
    next;
  } elsif($menu_line =~ /^\s*timeout/){
    $menu_line =~ s/\d+/$orig_timeout/;
    print TEMP_MENU $menu_line;
    next;
  }
  print TEMP_MENU $menu_line;
}
close MENU_LST;
close TEMP_MENU;
open TEMP_MENU, $TEMP_MENU_LST or die "Could not reopen temorary file: $!\n$ORIG_MENU_LST not modified\n";
open MENU_LST, "> $ORIG_MENU_LST" or die "Could not reopen $ORIG_MENU_LST for changes: $!\n$ORIG_MENU_LST not modified\n";
print MENU_LST "$_" while <TEMP_MENU>;
close MENU_LST;
close TEMP_MENU;
unlink $TEMP_MENU_LST or warn "Could not delete temporary file $TEMP_MENU_LST: $!\n";
print "Completed changing your default selection in menu.lst.\nThe backup file for your previous menu.lst is $BACKUP_FILE\n";

```

---

### Post by dwhitney67 on 2007-09-29
What you are doing is admirable, but isn't it a little overkill?

If I wanted to change my default OS, I would just edit the /boot/grub/menu.lst file and change this entry to the appropriate number:

default=<OS number>

The first OS (title) listed is '0' (zero), the next is '1', followed by '2', and so on.

A quick edit of the file is all that is needed.  I believe even a newb can handle that.

---

### Post by eph1973 on 2007-09-29
I thought it would be simple enough, also.  However, I've seen one or two people still apparently confused about it after it was explained to change the default that way.  Perhaps I have just wasted my time, though, as someone who can't figure out how to edit menu.lst probably can't figure out how to make a perl script executable, either.  Thanks for the feedback.

---

### Post by dwhitney67 on 2007-09-30
I wouldn't give up.  If indeed you are targeting the newbs, then perhaps a graphical interface is missing from your plans.  Perhaps something that can be invoked from the **System -> Administration** pull-down menu.

---

### Post by slavik on 2007-09-30
eph1973, your script is something similar to debian's alternatives thing (which also just manage symlinks).

This is a good project! :thumbsup: (and it's in Perl to boot ^^)

---

