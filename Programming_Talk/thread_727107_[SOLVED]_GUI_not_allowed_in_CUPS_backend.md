---
title: "[SOLVED] GUI not allowed in CUPS backend?"
date: 2008-03-17
forum: Programming Talk
---

### Post by run4flat on 2008-03-17
Greetings all -

I am trying to create a backend that will help me do manual duplexing with my printer.  It would be considered a general ps printer; it would take the ps given it and then use pstops to split things up, rotate, reorder, etc.  You get the idea.  After the first set of pages has printed, I would then want to display a little message dialog box saying, "Put the pages back in the paper tray and click 'OK' to continue."  Simple enough right?

Unfortunately, it seems that cups does not like GUI commands in the backend programs.  Here's some perl code to demonstrate:

[PHP]#!/usr/bin/perl
use strict;
use warnings;
use File::Basename;
#use Gtk2 '-init';

if($#ARGV == -1)
{
	# This is necessary for cups to 'see' the backend.  See man backend for details
	my $progname = basename($0);
	print "file $progname \"Unknown\" \"Silly Printer\"\n";
}
[/PHP]

Save this as 'sillyprint.pl', copy it to the backend directory and set the appropriate permissions:
```
chmod a+x sillyprint.pl; sudo cp sillyprint.pl /usr/lib/cups/backend
```

Now, if you go to System->Administration->Printing and select New Printer (or Edit->New Printer) you will see Silly Printer as one of your options.  Adding this printer won't do anything, of course, but that's OK, it's just a demonstration.

Now, uncomment the line ```
#use Gtk2 '-init';
```copy and set permissions as before and try to add a new printer.  Cups doesn't see it anymore!  The appropriate discovery text still displays (you can test that yourself by going to the backend directory and executing the script).  I haven't even done any GUI stuff, just enabled it.

I also tried pushing the GUI stuff to a separate script and determined that the script did not run at all.  Is this a matter of permissions?  Does the user `lp' lack access to graphical stuff?  Is there a way to change that?  Are there safety issues opposing such a change?

EDIT: Forgot to mention, yes I read the FAQ.  I tried Googling this, but I could not think of any search terms that would yield non-extraneous results.

---

### Post by mssever on 2008-03-17
GUIs depend on the environment variable $DISPLAY being set properly. Check that that's correct. Also, since cups runs as its own user, there might be X-related permissions issues you'll have to solve.

Question: How should cups know which display to send its notice to. Suppose the system has multiple sessions active. Checking username isn't necessarily enough, because a single user can have multiple sessions.

---

### Post by Zwack on 2008-03-17
CUPS allows remote printing.  If someone prints to "sillyprinter" from a windows box on a different network, where should the pop up message appear and how?  It is possible that CUPS has a "No gui" policy explicitly set somewhere.  But even if that isn't the case how do you plan on dealing with remote users?  There is no way that the CUPS backend can tell that you aren't going to.

Z.

---

### Post by run4flat on 2008-03-17
Thanks for your responses.

@mssever
> GUIs depend on the environment variable $DISPLAY being set properly.
When I'm running a shell on my machine, $DISPLAY is set to ``:0.0''  After a bit of fiddling, I was able to ensure that the $DISPLAY env variable was set to the same just before calling the Gtk2 script using this code:
[PHP]my $retval = `export DISPLAY=:0.0; ./sillygtk.pl`;[/PHP] but that did not solve my problem.  The script still did not run, so I'm guessing it's not that simple.

@mssever & Zwack
I have a printer that doesn't have buttons on it (HP 1020), so I'm pretty sure that the only way to get manual duplexing is through some sort of software.  So, where would this window show up?  On the server's box, of course, because the user would have to go to the printer in order to pull the paper out and put it back in. Honestly, it's really just meant to be a personal hack to make my life a little easier and I guess I'm asking cups to do somersaults for me.  Oh well.

If I end up creating some sort of pop-up server, I'll post it here.  Let me know if you have any other ideas and again, thanks for your responses.  If anybody else is reading along and would like some references, see 
[http://www.cups.org/newsgroups.php?s1+gcups.development+v1+T+Q%22GTK+Calls+from+CUPS+Backend%22](http://www.cups.org/newsgroups.php?s1+gcups.development+v1+T+Q%22GTK+Calls+from+CUPS+Backend%22)
(Note that I disagree with the first response of Michael Sweet: the commands are run as lp, not as root.)

Note: To anybody who is reading this and doesn't already know, you can set a great deal of information using PPDs and there is almost no information that you need to communicate that cannot be set with these when the job is submitted.  Of course, "I've flipped the pages, continue printing" cannot be sent when the job is submitted.;)

---

### Post by mssever on 2008-03-17
Another potential factor is X permissions. I don't understand it very well, but I know that in most cases, you can't access an X session you don't own. Of course, the existance of programs like gksudo demonstrates that there are ways around this.

In the thread you linked to, it was suggested to use named pipes to communicate. If you could only submit part of the job, then call an external program to pop up a GUI, then use the named pipe to grab the status of that program, then submit the second half of the job, that might work.

---

### Post by slavik on 2008-03-17
why not just print odd pages first, then even pages? anything using the gnome/kde dialogs should be able to do that ...

or you could use zenity for notifications/dialogs?

---

### Post by run4flat on 2008-03-18
@mssever:
Yeah, I'm actually in the middle of working with named pipes to solve the problem, in tandem with simple dialogs, which brings me to:

@slavik:
Thanks for the tip about Zenity!  Putting Zenity into the backend itself doesn't work, but I can use it in my popup server*, thus saving me a lot of trouble rolling my own code for a simple messagebox interface.  That's great! <thumbsup />  As for printing the even pages and then the odd pages, it's a laziness/matter-of-principle thing.  :]

So, I guess at this point, my problem has been turned into creating a Zenity server.  That seems funny - you might think that somebody would have already created one, but I couldn't find one via google.  Once I've got that, I can use the server in my backend to get the user input.


* - If I write a program that starts when the user logs on and ends when the user logs off which monitors a named pipe or a socket, that's called a server, right?  It's hard to find web definitions that care about anything besides an web or sql server, but those that I have found seem to agree.

---

### Post by run4flat on 2008-03-18
So I've written a Zenity server.  It's not exactly production quality but it seems to solve my problem.  In particular, I'm not sure where I should actually have the pipe: /tmp/ZenityServerPipe seems OK, but I'm sure there are more appropriate locations.

I tried to include some basic security features, such as removing semi-colons and attempting to prevent feedback loops that (might) cause problems.  I could not find guidelines for making secure programs, so any pointers here would be nice.


[PHP]#!/usr/bin/perl
use strict;
use warnings;

my $pipename = "ZenityServerPipe";
my $fullpipename = "/tmp/$pipename";

# ensure that the pipe exists and that we can read from it
use POSIX qw(mkfifo);
mkfifo($fullpipename, 0700) or Logger("ERROR: Could not create pipe $fullpipename: $!",
	"done") unless (-e $fullpipename);
Logger("ERROR: Cannot read from the pipe", "done") unless (-r $fullpipename);

my $pipeback;
my $zenityoptions;
my $retval;

while(1) {
	if(open (PIPEIN, "<$fullpipename")) {
		while($zenityoptions = <PIPEIN>) {
			exit(0) if ($zenityoptions =~ m/^end$/);
			
			# no semicolons
			$zenityoptions =~ s/;//g;
			
			# no feedback loops (since this might cause memory problems?)
			$zenityoptions =~ s/$pipename//g;
			
			# allow for newlines
			$zenityoptions =~ s/\\n/\n/g;
			
			# note, pipes are allowed since the calling program will likely get
			# the return info from a named pipe.
			`zenity $zenityoptions`;
		}
	close PIPEIN;
	}
}

sub Logger {
	my $string = shift @_;
	my $done = "false";
	if($#_ > -1 && $_[0] eq "done") {
		$done = "true";
	}
	# thanks to http://www.netadmintools.com/art212.html for this timestamp code:
	(my $sec,my $min,my $hour,my $mday,my $mon,my $year,my $wday,my $yday,my $isdst)
		=localtime(time);
	my $success = "true";
	open(OUTPUT, ">>/tmp/popuppipe.log") or $success='false';
	if($success eq "false") {
		print "Unable to record this message in the log: $string\n";
		return "failure" if($done eq "false");
		die "Unable to record this message in the log: $string" if ($done eq "true");
	}
	else {
		my $myoutstring = sprintf "%4d-%02d-%02d %02d:%02d:%02d\t$string\n",
			$year+1900,$mon+1,$mday,$hour,$min,$sec;
		printf OUTPUT $myoutstring;
		close OUTPUT;
		return "success" if ($done eq "false");
		die $myoutstring if ($done eq "true");
	}
}
[/PHP]

---

### Post by run4flat on 2008-03-18
Oh yeah, a brief explanation.

Be sure to start the server:
```
./ZenityServer &
```

The use the server, send your Zenity command options to the pipe, ending with an EOL and EOF.  For example, at the prompt you could type
```
cat > /tmp/ZenityServerPipe
--info text="This is an information box." > results.txt
<CTRL-D>
```
The last part is important and indicates where the results returned from Zenity will go.  If you are using this in cups or a similar server that does not have access to GUI capabilities, you'll want to create a named pipe and send the results to said named pipe.

---

