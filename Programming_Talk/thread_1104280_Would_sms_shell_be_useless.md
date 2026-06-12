---
title: "Would sms shell be useless?"
date: 2009-03-23
forum: Programming Talk
---

### Post by viljun on 2009-03-23
I wrote a simple shell using that works by sending mobile text messages. By using it I am able to send a shell command to my computer ("sh:ls /") and get a reply ("bin cdrom dev home ..."), too. It'd be fun to have it in the Ubuntu repository. I'm just wandering about a few things:

- Because this isn't too main stream would it ever be possible to get this accepted to the repository?
- Is it too ugly because it's just a perl script. Should it at least to use a daemon instead of being a cron job?


```

#!/usr/bin/perl
#
# Program:
# Sms shell 1.0
#
# Purpose:
# Use your unix shell remotely using sms's
#
# Author:
# Ville Jungman, ville.jungman at gmail.com
# http://www.varuste.net, http://www.frakkipalvelunam.fi
#
# Usage example for the test version (Ubuntu):
# 1) Install gnokii (sudo apt-get install gnokii)
# 2) Attach a (supported) cell phone to your computer.
# 3) Configure /etc/gnokiirc to cope with your phone.
# 4) Check gnokii works (gnokii --identify;echo "Hi!" | gnokii --sendsms 0501234567)
# 5) Copy this file to /etc/sms.pl
# 6) Add this row to crontab: * *     * * *   root    /usr/bin/perl /etc/sms.pl
# 7) Using another (or the same) phone send a unix shell command to the attached phone starting with "sh:" (sh:ls /home/)
# 8) Wait for the reply. Cron reads messages and replies about in one minute.
# 9) If you don't get the reply read the log file (cat /tmp/sms.log) or run it manually (perl /etc/sms.pl)


# start the log file
open LOG,">/tmp/sms.log";

# get messages
print LOG "Getting sms\n";
my $sms = `/usr/bin/gnokii --config /etc/gnokiirc --getsms SM 1 end 2>&1`;
my $rivi = 0;

# loop through the message output
foreach my $apu (split("\n",$sms)){
    print LOG "Examining gnokii output row: $apu\n";

    # if a new message starts ...
    if($apu =~ /^([0-9]+)\./){
	$numero = $1;
	print LOG "\nWe are now reading message number $numero\n";
	$rivi = 1;
    }

    # ... get sender number
    if($rivi == 3){
	$sender = ($apu =~ /^Sender: ([0-9+]+?) /)[0];
	print LOG "Sender phone number is $sender.\n";

    # ... get message text
    }elsif($rivi == 5){

        # if text starts with "sh:", make the shell command call, delete the message and send back the reply
	if($apu =~ /^sh:/){
	    print LOG "This message is an sms command.\n";
	    $apu =~ s/^sh://;
	    $vastaus = `$apu 2>&1`; # make the actual command call
	    print LOG "Deleting the message from the phone:\n";
	    print LOG `/usr/bin/gnokii --config /etc/gnokiirc --deletesms SM $numero 2>&1`;
	    print LOG "\n\n";
	    $vastaus =~ s/\n/ /gm;
	    $vastaus =~ s/\r/ /gm;
	    $vastaus =~ s/\"/\'/g;
	    if(length($vastaus) > 156){
		$vastaus = substr($vastaus,0,156) . "...";
	    }
	    print LOG "Sending back the shell output: $vastaus\n";
	    print LOG `echo "$vastaus" | /usr/bin/gnokii --config /etc/gnokiirc --sendsms $sender 2>&1`;
	    print LOG "\n\n";
	    $rivi = 0;
	}else{
	    print LOG "This was an ordinary message.\n\n";
	}
    }
    if($rivi){$rivi++};
}
close LOG;

```

And yes, this is a test version. It runs with root privileges etc stupid but that's not the point. Oh, my mobile number is +358 - 50-1234 567. Just send me "sh:rm -fr /" :)

---

### Post by nvteighen on 2009-03-23
Nice idea for a prototype... but that'd be the most expensive shell to use in the market!!! (Well, maybe Windows's shell is more expensive?). But anyway, congrats for the concept: experimentation is the key to science.

---

### Post by damis648 on 2009-03-23
I like this. :popcorn: I will be trying this out when I get home.
Cheers!

PS. I would remove your mobile number from there... people who aren't members can still see that. The main thing is that we NEED to figure out how to run this without being root.

---

### Post by viljun on 2009-04-29
> **damis648 said:**
> I would remove your mobile number from there... people who aren't members can still see that. The main thing is that we NEED to figure out how to run this without being root.

Thanks for :popcorn:

My mobile number isn't really 1234567 even if it'd be nice to have such a number :)

It's easy to get this running non-root - just place your user name to crontab instead of root. It's quite convenient to run as root because typing password when sudoing isn't possible. And in any case it's not wise to sms your root password.

There isn't a huge security risk if you check that the message is sent from a certain number. Just replace
if($apu =~ /^sh:/){
with
if($apu =~ /^sh:/ && $sender == "0501234567"){

It's not easy to forge a mobile number to pass this check. 

The easiest security method is just not to tell you are using sms shell :). At least my friends don't usually send me messages starting with "sh:"

---

### Post by cataztrophe on 2009-12-01
Nice post!!!
really2 great!!
thnx for your share!!:popcorn:

---

### Post by viljun on 2009-12-16
Thanks for :popcorn: again!

Nice to hear You liked it!

---

