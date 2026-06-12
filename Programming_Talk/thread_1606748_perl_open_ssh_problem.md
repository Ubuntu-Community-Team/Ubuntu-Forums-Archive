---
title: "perl open ssh problem"
date: 2010-10-26
forum: Programming Talk
---

### Post by samohung390 on 2010-10-26
hello, can anyone help me with this problem? im just a beginner and currently starting to program in perl, also i just installed openssh because what i really need is to ssh to a ubuntu server.
so I tried my code:
#!/usr/bin/perl

use strict;
use warnings;
use Net::OpenSHH;

my $ssh = Net::OpenSSH->new('IPAddress');
$ssh->error and die "ssh connection failed: ". $ssh->error;

my problem is that it keeps returning errors that I dont understand, it says:
use of uninitialized value $default_stdin_fh in anonymous hash....
almost the whole errors says like this but changes to $default_stdout_fh,$default_stderr_fh,$master_stdin_fh........


what does these error mean?

---

### Post by slavik on 2010-10-27
would be nice if you could post the actual errors.

---

