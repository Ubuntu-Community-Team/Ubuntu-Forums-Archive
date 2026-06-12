---
title: "Critique this Perl script (this could actually be useful to some of you)"
date: 2008-08-06
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-06
I wrote this tiny code as a brief introduction for myself to regex a couple weeks ago: [http://ubuntuforums.org/showthread.php?t=862851](http://ubuntuforums.org/showthread.php?t=862851)

Now it's grown to something that some of you might actually want to use (I saw some requests for an alarm program a while ago when I first joined), and I have a launcher on my panel and use this every night.

In the last 4-5 days I've modified it to be a full-blown (over 250 lines :p) alarm script with a lot of features:
[list]
[*]GUI entries that *should* pretty hard for the user to mess up
[*]Lots of error checking to see if everything will run correctly
[*]Cross-platform capabilities (should run on quite a few Linux distros with default settings, all the *buntus should work)
[*]Support for 12 and 24-hour clocks
[*]Good documenting/comments to see what is going on
[/list]

So I was hoping you guys could try it out and let me know what I could have done better (this is the largest program I've ever written; I'm pretty new at this).  I'm especially interested in whether people can get it to malfunction :).  If so please tell me what went wrong so I can fix it.  I think I've error tested it pretty hard, but I made some changes today so there could be some things I missed.

Anyway, the source code is pretty self-explanatory.  If you decide to edit the source code, try to follow the editing instructions I talk about at the start.  These are just quick changes that can be made, so don't consider these errors if you can mess it up by entering incorrect stuff in constants at the beginning :lolflag:.  I can integrate those things into the GUI later with proper error-checking.

Thanks a whole lot to anyone who gives some feedback, and let me know if you actually end up using this practically like I do :).



To run it, copy+paste and save the following in a text file anywhere, like ~/Documents/alarm.  Then navigate to that directory in the terminal and type 'chmod 700 alarm'.  Then you can run it with ./alarm from that directory, or by double-clicking it in the GUI.

```

#!/usr/bin/env perl
use strict;
use warnings;

# Alarm program - Play an audio file at a specified time
#
#
#
# This program uses 'aumix' to control the volume; this may not be a default
# installation on your distribution.  On Ubuntu it can be installed with
# "sudo apt-get install aumix".  If you do not desire volume control
# or cannot install aumix, change the 'Y' below to 'N'.
#
    use constant AUMIX => 'Y';
#
#
# To change the alarm volume from the default 100 %, change the number on
# the line below to the desired setting.  The volume will turn up to this
# percentage just before the audio file is opened, so the computer may be
# left muted or turned down overnight.  Adjust your speaker volume and this
# setting accordingly.  This will have no effect if the AUMIX setting
# above is set to 'N'.
#
    use constant VOLUME => 100;
#
#
# The default command to open the audio file is 'xdg-open', which should
# be able to open files in GNOME, KDE, and Xfce.  If you get an error
# regarding the lack of existence of your media player, change 'xdg-open'
# in the line below to a media player that will open your audio files, for
# example 'banshee-1', 'totem', or 'amarok'.  The spelling/case should be
# the same as if you were to run the application from the command line.
#
    use constant OPEN_COMMAND => 'xdg-open';
#
#
# If you would rather use a 24-hour clock than a 12-hour, change the 'N'
# on the line below to 'Y'.
#
    use constant TWENTYFOUR_HR_CLOCK => 'N';
#
#
#
# Written by Connor Manning
# August, 2008


{
    exit(1) unless(&checkMediaPlayer);
    exit(2) unless(&checkClockType);

    my($userHour, $userMin, $displayTime) = &getAlarmAttributes;
    my $file = &getFile;

    &alarm($file,
           &formatConfirmation($displayTime, $file),
           &calculateSleepTime($userHour, $userMin));

    exit(0); # end of main
}

#----------------------------------------------------------------------

# checks for the existence of media player
sub checkMediaPlayer {
    my $command = OPEN_COMMAND;
    if(`which $command`){
        return 1;
    } else {
        my $error = 'zenity --error --text="Invalid media player - ' . 
                    "does not exist\n\nView source code for details\n\n" .
                    "\n\nAlarm not set\"";

        `$error`;
    }
    0;
}

#----------------------------------------------------------------------

sub checkClockType {
    if(TWENTYFOUR_HR_CLOCK eq 'Y' || TWENTYFOUR_HR_CLOCK eq 'N'){
        return 1;
    } else {
        my $error = "zenity --error --text=\"Invalid clock setting\n\n" .
                    "View source code for details\n\n\n\nAlarm not set\"";

        `$error`;
    }
    0;
}

#----------------------------------------------------------------------

# returns the hour of the alarm in converted 24-hour format, the minute,
# and a formatted time to display to the user
sub getAlarmAttributes {

    my $userTime = &getTime;

    # grab needed variables from user entry, translate setting to lower case
    my($userHour, $userMin, $setting);
    if($userTime =~
      m/^\s*(0?\d|1[0-2])\s*:\s*([0-5]\d)\s*([ap])\s*m?\s*$/i){

        ($userHour, $userMin, $setting) = ($1, $2, $3);
        $setting =~ tr/[P]/[p]/;
    } elsif($userTime =~ m/^\s*(0?\d|1\d|2[0-3])\s*:\s*([0-5]\d)\s*$/){
        ($userHour, $userMin) = ($1, $2);
    }

    # create formatted time to display to the user at confirmation dialog
    my $displayTime;
    if(TWENTYFOUR_HR_CLOCK eq 'N'){
        $displayTime = sprintf "%d:%02d %s", $userHour, $userMin,
                       $setting eq 'p' ? "pm" : "am";
    } else {
        $displayTime = sprintf "%02d:%02d", $userHour, $userMin;
    }

    # adjust hour of the alarm to 24-hour clock if needed (to coincide 
    # with 'localtime' function) for am/pm entries
    my $updatedHour;
    if(TWENTYFOUR_HR_CLOCK eq 'N'){
        if($userHour == 12){
            $updatedHour = $setting eq 'p' ? 12 : 0;
        } else {
            $updatedHour = $setting eq 'p' ? $userHour + 12 : $userHour;
        }
    } else {
        $updatedHour = $userHour;
    }

    ($updatedHour, $userMin, $displayTime);
}

#----------------------------------------------------------------------

# returns raw time string after regex check for proper format
sub getTime {
    my $timeCommand = 'zenity --entry ' .
                      '--title="Set the Alarm Time" ' .
                      '--text="Set the alarm time in '; 

    $timeCommand .= TWENTYFOUR_HR_CLOCK eq 'N' ? '12-hour am/pm format:"' :
                    '24-hour format:"';

    my $userTime = "";

    if(TWENTYFOUR_HR_CLOCK eq 'N') {
        until($userTime =~
                m/^\s*(0?\d|1[0-2])\s*:\s*([0-5]\d)\s*([ap])\s*m?\s*$/i){

            chomp($userTime = `$timeCommand`);
            exit if $?;
        }
    } elsif(TWENTYFOUR_HR_CLOCK eq 'Y'){
        until($userTime =~ m/^\s*(0?\d|1\d|2[0-3])\s*:\s*([0-5]\d)\s*$/){
            chomp($userTime = `$timeCommand`);
            exit if $?;
        }
    }
    $userTime;
}

#----------------------------------------------------------------------

# returns selected audio file string, error checked with regex of the
# Bash `file` command with the --mime option (-i)
sub getFile {
    my $fileCommand = 'zenity --file-selection ' . 
                      '--title="Select an Audio File" ' .
                      '--filename=~/Music/';

    chomp(my $file = `$fileCommand`);
    exit if $?;

    # make sure file is an audio file
    unless(`file -i "$file"` =~ m/$file: audio.+/i){
        my $error = 'zenity --error --text="Invalid file selection - ' . 
                    "not an audio file\n\nAlarm not set\"";
        `$error`;
        exit(3);
    }
    $file;
}

#----------------------------------------------------------------------

# if the audio file fits the format of path/artist/album/song.extension,
# a confirmation message is formatted to display these attributes;
# otherwise, a generic message is formatted with the raw filename
sub formatConfirmation {
    my($displayTime, $file) = @_;

    my $message = "zenity --info --title=\"Alarm Set for $displayTime\" " .
                  '--text="The alarm was successfully set for ' .
                  "$displayTime.\n\n";

    if($file =~ m{/([^/]+)/([^/]+)/([^/]+)\.(.+)$}i){
        my($artist, $album, $song, $extension) = ($1, $2, $3, $4);

        $message .= "Song: $song\nAlbum: $album\nArtist: $artist\n\n" .
                    "Filetype: $extension";

    } else {
        $message .= "File: $file";
    }
    $message .= '"';
}

#----------------------------------------------------------------------

# displays confirmation in forked child process, while parent process
# sleeps until alarm activation time, allowing user to leave confirmation
# window open without the parent process explicitly waiting to reap it
sub alarm {
    my($file, $message, $sleepTime) = @_;

    # setting to reap zombie child process if dialog box is closed
    $SIG{CHLD} = "IGNORE";

    # fork() returns undef if forking process fails
    die "Cannot fork(): $!" unless defined(my $pid = fork());

    if($pid == 0){  # child process
        `$message`;
        exit;
    } else {        # parent process
        sleep($sleepTime);
        my($program, $vol) = (OPEN_COMMAND, VOLUME);
        `aumix -v$vol` if(AUMIX eq 'Y');
        `$program "$file"`;
    }
    0;
}

#----------------------------------------------------------------------

# returns time until user's alarm time in seconds
sub calculateSleepTime {
    my($userHour, $userMin) = @_;
    my($sec, $min, $hour) = localtime;

    return 0 if($userHour == $hour && $userMin == $min);

    my $sleepTime = 60 - $sec;
    $min += 1;

    # if $userMin == $min, $sleepTime does not need to account for minutes
    if($userMin > $min){
        $sleepTime += 60 * ($userMin - $min);
    } elsif($userMin < $min){
        $sleepTime += 60 * (($userMin + 60) - $min);
        $hour += 1;
    }

    if($userHour > $hour){
        $sleepTime += 60 * 60 * ($userHour - $hour);
    } elsif($userHour < $hour){
        $sleepTime += 60 * 60 * (($userHour + 24) - $hour);
    }
    $sleepTime;
}


```

---

