---
title: "aimbot with OSCAR"
date: 2008-08-25
forum: Programming Talk
---

### Post by shortridge11 on 2008-08-25
I'm trying to make an aimbot to run scripts so i can run scripts from my phone.  I'm brainstorming for ideas that would be really useful, but so far all i can think of is sending me a text alert at a specified time, and starting a torrent download.  Anyone have any great ideas?

---

### Post by jinksys on 2008-08-25
> **shortridge11 said:**
> I'm trying to make an aimbot to run scripts so i can run scripts from my phone.  I'm brainstorming for ideas that would be really useful, but so far all i can think of is sending me a text alert at a specified time, and starting a torrent download.  Anyone have any great ideas?

I once wrote an aimbot in perl that essentially let my chat window become a terminal, sort of like an AIM TELNET session.  

What sort of phone/service do you have?

---

### Post by shortridge11 on 2008-08-25
i have a verizon motorola razr V3m.  It somehow gets aim.  But this is also for when i'm on gmail or on my ipod touch.  I'm trying not to give too much freedom like making the bot a window to terminal, for obvious security reasons.  Do you know how to make the bot send a message the first time you talk to it?  As an example, if it was signed on for a while, and i sign on and say hi to it then it will reply with it's standard "hello".  And if i say something else to it that's not a command it will either say "that's not a command" or just not say anything at all (i haven't figured out which i want to do).  Also, if it was possible i wanted to use a timer so that it would respond with it's hello message again after a certain period of time.  And if possible if i signed off and back on.  i don't know if that one's possible though.

---

### Post by jinksys on 2008-08-25
Some Qs
What language are you writing the bot in?

How far along are you?

are you using a library for OSCAR or are you writing the protocol interface yourself?

---

### Post by shortridge11 on 2008-08-25
#!/usr/bin/perl

use strict;
use Net::OSCAR;
use LWP::Simple;

my $oscar = Net::OSCAR->new();
my $sn = 'EDIT';
my $pw = 'EDIT';
my $owner = 'EDIT';

sub im_in {
	
	my ($oscar, $sender, $message) = @_;	
	$message =~ s/<(.|\n)+?>//g;
	print "$sender: $message\n";
	
	if($sender eq $owner) { 	
		if ($message =~ /help/i) { 
			$oscar->send_im($sender, "External - Sends the external ip address I am running from.");
			$oscar->send_im($sender, "Help - Shows commands I can interpret.");
		}

		if ($message =~ /external/i) { 
			my $external_ip = get("http://whatismyip.org/");			
			$oscar->send_im($sender, "External IP: $external_ip"); 
		}
	}
	
	else { $oscar->send_im($sender, "I'm afraid you are not the owner"); }
}	

while(1) {
		
	my $oscar = Net::OSCAR->new();

	$oscar->set_callback_im_in (\&im_in);
	
	$oscar->do_one_loop();
        $oscar->signon($sn, $pw);
	while(!my $connection_closed) { 
		$oscar->do_one_loop();
	}
			
	my $connection_closed = 0;

}



i am using perl.
This is the skeleton i used to do it.  Basically all i have now is if something matches one of the words i have, then i do what's in that elsif, and if nothing matches then i don't do anything.  I've gotten the help, external (returns my ip), gui (determines if my gui is up and starts or stops it accordingly), display (shows my memory, hdd space, and users), reboot, and webcam service (activates my webcam service which starts capturing video if someone walks on screen).  I havn't gotten my alert (sends me an alert after a specified time) or torrent (starts torrent downloading on my bittorrent client, deluge).

---

