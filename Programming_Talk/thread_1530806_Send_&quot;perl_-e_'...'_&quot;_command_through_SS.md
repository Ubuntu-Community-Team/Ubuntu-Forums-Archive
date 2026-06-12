---
title: "Send &quot;perl -e '...' &quot; command through SSH, from a perl script"
date: 2010-07-14
forum: Programming Talk
---

### Post by clrg on 2010-07-14
Hey guys

I am trying to send a perl -e command to a number of systems using SSH. The command should retrieve some information for me. The problem is, the remote shell tries to interpolate my variables and doesn't get it should take the command literally and just execute it.

Below the code. You don't need to read all of it if you don't want to. The only problem I have is to send the command LITERALLY to the remote shell so it will be executed correctly, without anything in between behaving smart and interpolating variables or even executing parts of the code.

```

tgdhipa2@usoadm01:~$ cat getinfo.pl 
#!/usr/bin/perl
############################################################################
############################################################################
##                                                                        ##
##  Collect information from a list of machines                           ##
##  *******************************************                           ##
##                                                                        ##
##  Copyright (C) 2010  Patrick Hirt (patrick.hirt/at/gmail/dot/com)      ##
##                                                                        ##
##  This program is free software: you can redistribute it and/or modify  ##
##  it under the terms of the GNU General Public License as published by  ##
##  the Free Software Foundation, either version 3 of the License, or     ##
##  (at your option) any later version.                                   ##
##                                                                        ##
##  This program is distributed in the hope that it will be useful,       ##
##  but WITHOUT ANY WARRANTY; without even the implied warranty of        ##
##  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         ##
##  GNU General Public License for more details.                          ##
##                                                                        ##
############################################################################
############################################################################


use strict;
use warnings;

# **************************************************************************#
#   Configure program here                                                  #
#       Command to send to the machine.                                     #
#       The resulting string of this command                                #
#       will be displayed per hostname (if any)                             #
# **************************************************************************#
open(C, "<command");
my $command = <C>;
close(C);

# **************************************************************************#
#       Machines to check, seperate with a whitespace                       #
# **************************************************************************#
my @serverlist = qw( usoadm01 msunadm01 );

# **************************************************************************#
#   SSH command used to connect to the machines,                            #
#   in most cases does not need to be modified                              #
# **************************************************************************#
#my $sshcmd = "ssh -t -q -o " . "\"Batchmode yes\" " . "-o " . "\"ConnectTimeout 5\" " . "-l root ";
my $sshcmd = "ssh -t -q -o " . "\"Batchmode yes\" " . "-l root ";


# **************************************************************************#
# Don't modify program below here (unless necessary)                        # 
# **************************************************************************#
# Declare some stuff
my $sshreturn;
my %output;
my $k;
my @v;
my $count = 0;
my $pointcount = 0;
my $percentage;
my $p1 = 0;
my $p2 = 0;
my $p3 = 0;
my $total = @serverlist;

# Inform the use we're about to start working
print("Collecting information...\n");
# Iterate server list
foreach(@serverlist) {
        $count++;
        $pointcount++;
        if($pointcount == 3){
                print(".");
                $pointcount = 0;
        }
        $percentage = ($total / 100) * $count;
        if($percentage > 18 and $percentage < 22 and $p1 == 0){
                print(" 20% ");
                $p1 = 1;
        }
        if($percentage > 48 and $percentage < 52 and $p2 == 0){
                print(" 50% ");
                $p2 = 1;
        }
        if($percentage > 78 and $percentage < 82 and $p3 == 0){
                print(" 80% ");
                $p3 = 1;
        }
        $sshreturn = `$sshcmd $_ '$command'`;
        unless(!defined($sshreturn) or $sshreturn eq ''){
                $output{"$_"} = "$sshreturn";
        }
        undef($sshreturn);
}
print("\n\nDone!\n");
print "\n";

foreach $k (sort(keys(%output))){
        @v = sort(lc($output{"$k"}));
        foreach(@v){
                s/\n/ /g;
        }
        print("$k:\n@v\n\n");
}
exit(0);


```I'm sure you're wondering the contents of the "command" file.. Here you go:

```

perl -e 'my $keyf; my $foo; my $bar; my $comment; my @output; open(F, "</etc/ssh/sshd_config"); while(<F>){ if(m/AuthorizedKeysFile/){s/%u/root/; s/AuthorizedKeysFile //; $keyf = $_;}} close(F); open(K, "<$keyf"); while(<K>){chomp; ($foo, $bar, $comment) = split(/ /); $comment = $comment . " "; push(@output, $comment); $foo = undef; $bar = undef;} close(K);foreach(@output){print;}'

```Here is the error message I get when executing the script:
```

tgdhipa2@usoadm01:~$ perl getinfo.pl 
Collecting information...
sh: syntax error at line 1: `open' unexpected
<...>

```It is this error message that leads me to believe the remote shell doesn't understand that the string is a perl command, instead tries to execute it itself - which of course fails.

EDIT: I managed to solve part of the problem by removing the double quotes inside the command and replacing them with qq|<...>| . 

The error message now is:

```
bash: -c: line 0: syntax error near unexpected token `F,'
```

I assume I got around part of the quoting problem, although I don't understand why bash fails at F, and not at open().

Still in desperate need of help!

Thank you.

---

### Post by gmargo on 2010-07-14
It's difficult to escape everything properly.  If you put a "echo" before the 'perl', you'll get a better idea of what the other side is seeing.  However, since you have root access, why don't you just copy a script over to the remote's /tmp and execute that?

---

### Post by clrg on 2010-07-14
Thank you for your response.

I thought about that. Unfortunately, a SCP for every host would double  the time the script needs to run. I have 2600 machines to check, which  takes my script approx. 40 minutes (just with one SSH command). If it's  an scp and an ssh, it will take 2 hours.

I would like the script to be as fast as possible. If I don't find a  solution, I'll implement your suggestion.

---

### Post by slavik on 2010-07-14
> **clrg said:**
> Thank you for your response.

I thought about that. Unfortunately, a SCP for every host would double  the time the script needs to run. I have 2600 machines to check, which  takes my script approx. 40 minutes (just with one SSH command). If it's  an scp and an ssh, it will take 2 hours.

I would like the script to be as fast as possible. If I don't find a  solution, I'll implement your suggestion.
consider setting up an nfs server with whatever scripts you need to be available on remote systems. (ssh root@$host "echo 'mount line' >> /etc/fstab" needs to be run once).

Also consider using libssh (for perl of course) to open the connection instead of calling ssh on the command line.

---

### Post by clrg on 2010-07-23
I can't run a centralized NFS share due to the restrictive policy of our security department. You don't want to know what my boss had to do in order to get us SSH access to all machines ^^

Nah, I "solved" the problem by echoing the code into a file, executing it and deleting it afterwards. That way, no additional SSH connection initialization for SCP is necessary.

---

### Post by ghostdog74 on 2010-07-23
why don't you consider using a SSH module from CPAN? that way, you don't have make calls to external ssh command.

---

### Post by clrg on 2010-07-24
Because Net::SSH or how its called isn't installed on our HP-UX management machine (the only one having SSH access to all network zones), and our 'security' department expressively forbids us to install ANY kind of software.

---

### Post by slavik on 2010-07-24
> **clrg said:**
> Because Net::SSH or how its called isn't installed on our HP-UX management machine (the only one having SSH access to all network zones), and our 'security' department expressively forbids us to install ANY kind of software.
HP-UX? NOOOOOOOOOOOOOOOOOOOOOOOO!!!!

I gotta ask, what does your company do that the security department has such restrictions. (if you're allowed to answer of course).

Also, have you considered expect?

Here's another idea: Find out who needs this data and tell them to take it up with security. They can go up to CIO/CTO if need be. Where I work, we had a similar issue with one of our clients. It worked out in the end.

---

### Post by clrg on 2010-07-24
Our customers are banks and even more delicate things. So security is *KINDA* important. (And no, I'm not allowed to say this ^^)


My boss needs the data. And I won't escalate the issue to our CEO or CIO, since they both don't know what SSH even is. Consider the issue resolved :>

---

