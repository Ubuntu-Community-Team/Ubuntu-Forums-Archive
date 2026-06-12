---
title: "How to save an offline video i just watched on my browser without having to download"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by rpupa on 2012-04-16
I just watched a video from a website, and now i want to save it on my harddisk to watch it again later. i can watch the video on my browser disconnecting the internet, but how to save it on disk from the memory it is in, without having to download it again online from the site. I want to save bandwidth?

---

### Post by 3rdalbum on 2012-04-16
> **rpupa said:**
> I just watched a video from a website, and now i want to save it on my harddisk to watch it again later. i can watch the video on my browser disconnecting the internet, but how to save it on disk from the memory it is in, without having to download it again online from the site. I want to save bandwidth?

There is a magical incantation for this, but at the moment I am not near my computer. Do a search for "save Flash Linux" and find the most recent article you can on Google. There are a lot of old instructions that say "look in /tmp" but this no longer works.

---

### Post by rpupa on 2012-04-16
> **3rdalbum said:**
> There is a magical incantation for this, but at the moment I am not near my computer. Do a search for "save Flash Linux" and find the most recent article you can on Google. There are a lot of old instructions that say "look in /tmp" but this no longer works.
i did what it said
[LEFT]Step-1.  Open Mozilla or any of  your web browser and open  web page with the  video that you would like to download. Wait until the video loads  completely. Eg:  YouTube, you can see a  lighter red indicator bar  reached the right end side.

Step-2.  Open  /tmp folder (Places-->Computer-->Filesystem-->tmp).   Here you can see the flash video that you have just downloaded. The name  of the downloaded video file has the word "Flash" on it.

Step-3. Rename the video file with a .flv extension and save it to any folder you like.
[COLOR=#3333FF]****[/COLOR][/LEFT]
[COLOR=#3333FF][B]
[/B][/COLOR][LEFT]but it seems that there are no files with Flash in it. I just want to know , are all videos flash?
[COLOR=#3333FF]****[/COLOR][/LEFT]

---

### Post by ikt on 2012-04-16
> **rpupa said:**
> I just watched a video from a website, and now i want to save it on my harddisk to watch it again later. i can watch the video on my browser disconnecting the internet, but how to save it on disk from the memory it is in, without having to download it again online from the site. I want to save bandwidth?

Depends on what type of video and what type of measures they are using to stop people downloading it. If it's a simple flash embed it may be easy but if it's something from a big corporation:

[http://ikt.id.au/blog/2012/01/22/stephen-colbert-colbert-remix-challenge-remixing-is-ok-fffffffffffffffuuuuuuuuuuuuuuu-comedy-central/](http://ikt.id.au/blog/2012/01/22/stephen-colbert-colbert-remix-challenge-remixing-is-ok-fffffffffffffffuuuuuuuuuuuuuuu-comedy-central/)

---

### Post by rpupa on 2012-04-16
some simple videos from youtube are easy to download.
Just played the video in my browser, then open another tab and type "about:cache" then click the link in blue, then searched for the site or the large sized file/link and clicked it.
It instantly gives the file to save in a location.
But some videos are not like that, they don't even appear in the cache list, or anywhere,?

---

### Post by jonnyboysmithy on 2012-04-16
I think it was with gnash, you right click in the video window and select save. I maybe mistaken though..
Anyone want to check this out?

---

### Post by morkovka078 on 2012-04-16
.

---

### Post by lisati on 2012-04-16
Friendly reminder: [s][http://ubuntuforums.org/announcement.php?f=123](http://ubuntuforums.org/announcement.php?f=123)[/s] [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

### Post by s1baker on 2012-04-16
Here is a script that David Ljung Madison wrote that will allow you to copy a flash that you viewed so that you can save it.
I have a separate folder that I have this script in. After the flash vid is viewed/downloaded, I go to the folder and run this script.

```
#!/usr/bin/perl
# Filename:	flashcache
# Author:	David Ljung Madison <DaveSource.com>
# See License:	http://MarginalHacks.com/License/
# Description:	Copy flash files in your browsers cache
# Dependencies:	Unix command 'lsof'
use strict;

##################################################
# Setup the variables
##################################################
my $PROGNAME = $0; $PROGNAME =~ s|.*/||;

my $LSOF = 'lsof';

my $FIND = 'flash';	# Find flash files
my $POST = 'flv';	# Postfix to save to

# Where we save files
#   %f is $FIND
#   %d is the next available number
#   %p is .$POST
my $DEST = "found%f.%d%p";

##################################################
# Usage
##################################################
sub fatal {
	foreach my $msg (@_) { print STDERR "[$PROGNAME] ERROR:  $msg\n"; }
	exit(-1);
}

sub usage {
	foreach my $msg (@_) { print STDERR "ERROR:  $msg\n"; }
	print STDERR <<USAGE;

Usage:\t$PROGNAME [-d]
  Copies deleted flash files currently open in your browser's cache
  -d             Set debug mode
  -find <str>    What to search for  [default $FIND]
  -post <str>    Postfix for saving files [default $POST]
  -dest <str>    Or just specify full destination [default $DEST]
                 (see the script for meanings of %f, %d, %p)

USAGE
	exit -1;
}

sub parseArgs {
	usage("You need to be on a system that uses /proc") unless -d '/proc';

	my $opt = {
		find => $FIND,
		post => $POST,
		dest => $DEST,
	};
	while (my $arg=shift(@ARGV)) {
		if ($arg =~ /^-h$/) { usage(); }
		if ($arg =~ /^-d$/) { $MAIN::DEBUG=1; next; }
		if ($arg =~ /^-find$/) { $opt->{find} = shift(@ARGV); next; }
		if ($arg =~ /^-post$/) { $opt->{post} = shift(@ARGV); next; }
		if ($arg =~ /^-dest$/) { $opt->{dest} = shift(@ARGV); next; }
		if ($arg =~ /^-/) { usage("Unknown option: $arg"); }
		usage("Too many files specified [$arg and $opt->{file}]") if $opt->{file};
	}

	usage("You need to specify a destination with -dest")
		unless $opt->{dest};
	
	usage("You need to specify something to search for with -find")
		unless $opt->{find};
	
	$opt;
}

sub debug {
	return unless $MAIN::DEBUG;
	foreach my $msg (@_) { print STDERR "[$PROGNAME] $msg\n"; }
}

##################################################
# Main code
##################################################
sub findFiles {
	my ($opt) = @_;
	my @found;
	# 'lsof /'  (The '/' just does files, no sockets, and is faster)
	open(LSOF,"$LSOF /|") || usage("Can't run [$LSOF]");
	while (<LSOF>) {
		next unless /delete/i;
		next unless /\Q$opt->{find}\E/i;
		chomp;
		# procname  pid  user   fd
		usage("Found it, can't parse it [$_]")
			unless /^\S+\s+(\d+)\s+\S+\s+(\d+)/;
		push(@found, [$1,$2]);
	}
	usage("Couldn't find any deleted cached $opt->{find} files")
		unless @found;
	@found;
}

sub procPath {
	my ($pid,$fd) = @_;
	my $path = "/proc/$pid";
	usage("Couldn't find $path") unless -d $path;
	$path .= '/fd';
	usage("Couldn't find $path") unless -d $path;
	$path .= "/$fd";
	usage("Couldn't read $path") unless -e $path;
	$path;
}

sub destPath {
	my ($opt) = @_;
	my $p = $opt->{dest};
	$p =~ s/%f/\Q$opt->{find}\E/g;
	$p =~ s/%p/.\Q$opt->{post}\E/g;
	my $num = 0;
	my $path;
	do {
		$path = $p;  $num++;
		$path =~ s/%d/$num/g;
	} until ! -f $path;
	$path;
}

sub main {
	my $opt = parseArgs();
	
	my @found = findFiles($opt);
	foreach my $found ( @found ) {
		my $src = procPath(@$found);
		my $dest = destPath($opt);
		print "$src -> $dest\n";
		system("/bin/cp",$src,$dest);
	}
}
main();
```

---

### Post by rpupa on 2012-04-16
I downloaded the gnash but don't know how to use it to view online video and then save it. The firefox seems to be playing video with default flash player.......?

---

### Post by rpupa on 2012-04-16
> **s1baker said:**
> Here is a script that David Ljung Madison wrote that will allow you to copy a flash that you viewed so that you can save it.
I have a separate folder that I have this script in. After the flash vid is viewed/downloaded, I go to the folder and run this script.

```
#!/usr/bin/perl
# Filename:	flashcache
# Author:	David Ljung Madison <DaveSource.com>
# See License:	http://MarginalHacks.com/License/
# Description:	Copy flash files in your browsers cache
# Dependencies:	Unix command 'lsof'
use strict;

##################################################
# Setup the variables
##################################################
my $PROGNAME = $0; $PROGNAME =~ s|.*/||;

my $LSOF = 'lsof';

my $FIND = 'flash';	# Find flash files
my $POST = 'flv';	# Postfix to save to

# Where we save files
#   %f is $FIND
#   %d is the next available number
#   %p is .$POST
my $DEST = "found%f.%d%p";

##################################################
# Usage
##################################################
sub fatal {
	foreach my $msg (@_) { print STDERR "[$PROGNAME] ERROR:  $msg\n"; }
	exit(-1);
}

sub usage {
	foreach my $msg (@_) { print STDERR "ERROR:  $msg\n"; }
	print STDERR <<USAGE;

Usage:\t$PROGNAME [-d]
  Copies deleted flash files currently open in your browser's cache
  -d             Set debug mode
  -find <str>    What to search for  [default $FIND]
  -post <str>    Postfix for saving files [default $POST]
  -dest <str>    Or just specify full destination [default $DEST]
                 (see the script for meanings of %f, %d, %p)

USAGE
	exit -1;
}

sub parseArgs {
	usage("You need to be on a system that uses /proc") unless -d '/proc';

	my $opt = {
		find => $FIND,
		post => $POST,
		dest => $DEST,
	};
	while (my $arg=shift(@ARGV)) {
		if ($arg =~ /^-h$/) { usage(); }
		if ($arg =~ /^-d$/) { $MAIN::DEBUG=1; next; }
		if ($arg =~ /^-find$/) { $opt->{find} = shift(@ARGV); next; }
		if ($arg =~ /^-post$/) { $opt->{post} = shift(@ARGV); next; }
		if ($arg =~ /^-dest$/) { $opt->{dest} = shift(@ARGV); next; }
		if ($arg =~ /^-/) { usage("Unknown option: $arg"); }
		usage("Too many files specified [$arg and $opt->{file}]") if $opt->{file};
	}

	usage("You need to specify a destination with -dest")
		unless $opt->{dest};
	
	usage("You need to specify something to search for with -find")
		unless $opt->{find};
	
	$opt;
}

sub debug {
	return unless $MAIN::DEBUG;
	foreach my $msg (@_) { print STDERR "[$PROGNAME] $msg\n"; }
}

##################################################
# Main code
##################################################
sub findFiles {
	my ($opt) = @_;
	my @found;
	# 'lsof /'  (The '/' just does files, no sockets, and is faster)
	open(LSOF,"$LSOF /|") || usage("Can't run [$LSOF]");
	while (<LSOF>) {
		next unless /delete/i;
		next unless /\Q$opt->{find}\E/i;
		chomp;
		# procname  pid  user   fd
		usage("Found it, can't parse it [$_]")
			unless /^\S+\s+(\d+)\s+\S+\s+(\d+)/;
		push(@found, [$1,$2]);
	}
	usage("Couldn't find any deleted cached $opt->{find} files")
		unless @found;
	@found;
}

sub procPath {
	my ($pid,$fd) = @_;
	my $path = "/proc/$pid";
	usage("Couldn't find $path") unless -d $path;
	$path .= '/fd';
	usage("Couldn't find $path") unless -d $path;
	$path .= "/$fd";
	usage("Couldn't read $path") unless -e $path;
	$path;
}

sub destPath {
	my ($opt) = @_;
	my $p = $opt->{dest};
	$p =~ s/%f/\Q$opt->{find}\E/g;
	$p =~ s/%p/.\Q$opt->{post}\E/g;
	my $num = 0;
	my $path;
	do {
		$path = $p;  $num++;
		$path =~ s/%d/$num/g;
	} until ! -f $path;
	$path;
}

sub main {
	my $opt = parseArgs();
	
	my @found = findFiles($opt);
	foreach my $found ( @found ) {
		my $src = procPath(@$found);
		my $dest = destPath($opt);
		print "$src -> $dest\n";
		system("/bin/cp",$src,$dest);
	}
}
main();
```
In what folder should i save the script, and in which folder is the supposed to be saved.........confused.

---

### Post by morhin on 2012-04-17
I just replied to another thread you got started along these same lines. 

The easiest thing I've found is do "google" DownLoadHelper. It's a plugin for most browsers including Firefox.
 It's almost too easy to use.

By the way..... I'm not sure I know of a way to save anything without downloading it unless you just save the url. But then I'm no geek.

Morhin

:-)

---

### Post by s1baker on 2012-04-19
@rpupa

do this :
 First, make a folder in your home directory. I called mine "scripts"

1)  Copy the script file. ( hold down left mouse button and
select all of the script file. Release left button and hit right button of the mouse and select copy ) 
2)  Open gedit and paste the file in it ( hit right button
on the mouse and select "paste" )
3)  Save the file in the folder that you created
4)  Give the script file a name, anything will do. ( I just called mine "flashcache" ), and
you don't need to give the name an extension.
4)  'right' click on this file.
5)  Select properties and then permissions and check the "allow executing the file as a program". Now you are set to go.

6)  After you watch a .flv file on your browser , or otherwords, after it has downloaded, go to the folder where
the script file is and 'left' click on the script file with the mouse.
7) You should see options saying that it is an executable text file. 'left' click the mouse on "run".

 8) After it runs, you should see a file appear in the folder. This is the last flv file you just watched. It will probably be named "foundflash.1.flv"
Rename it what you want.
9) You should be able to open it and view it with "movieplayer" or "vlc" player, or whatever
you use to view flv files.

~Also, you may want to get the add-on "downloadhelper" for Firefox

---

