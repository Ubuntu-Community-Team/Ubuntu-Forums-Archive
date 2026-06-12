---
title: "Conky mail script"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-01
I would like to show new mail count for my Yahoo, Gmail and Hotmail. Can anyone point me to the right direction. Thanks

---

### Post by RavUn on 2008-08-01
[http://ubuntuforums.org/showthread.php?t=451128&highlight=conky+mail](http://ubuntuforums.org/showthread.php?t=451128&highlight=conky+mail)

add to conky: 
```
${texeci 600 /home/YOUR_NAME/scripts/email.pl}
```

Create the email.pl file:
```

#!/usr/bin/perl

# beginning of configuration

# pop3 host
$pop_host = "pop_server";

# pop3 username 
$pop_user = "usr_name";

# pop3 password
$pop_pass = "password";

# ssl port number
$ssl_port = "995";

# ssl protocol
$ssl_prot = "tcp";

# number of emails to show
$dis_numb = "5";

# end of configuration

use Mail::POP3Client;
use IO::Socket::SSL;

  my $socket = IO::Socket::SSL->new( PeerAddr => $pop_host,
                                     PeerPort => $ssl_port,
                                     Proto    => $ssl_prot);
  my $pop = Mail::POP3Client->new();
  $pop->User($pop_user);
  $pop->Pass($pop_pass);
  $pop->Socket($socket);
  $pop->Connect();

$msg_count = $pop->Count();

for ($i = $msg_count, $j = 0; $i >= $msg_count-($dis_numb-1); $i--, $j++) {
  foreach ( $pop->Head( $i ) ) {
    #/^(From|Subject):\s+/i and print $_, "\n";
    if ($_ =~ m/^From:/) {
      ($from) = ($_ =~ m#^From: .*<(.*)>#);
      $from = substr($from, 0, 30);
      $out .= "$j = $from\n";
    }
  }
  #chop $out;
  `echo -e "$out"> ~/.gmail/.gmail_top`;
}

$pop->Close();
```

For gmail, I think the pop server is pop.gmail.com... put in your username and password


I'm just snipping that from the OP... You may want to read the thread for more info.

---

### Post by Gargintua on 2010-01-20
hey this script sounds promising but only works until line 25, because i get this error.

```

Conky: desktop window (1e00d6b) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x5800001)
Conky: drawing to double buffer
Can't locate Mail/POP3Client.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/gargintua/scripts/email.pl line 25.
BEGIN failed--compilation aborted at /home/gargintua/scripts/email.pl line 25.
Can't locate Mail/POP3Client.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/gargintua/scripts/email.pl line 25.
BEGIN failed--compilation aborted at /home/gargintua/scripts/email.pl line 25.

```

my script looks like this excluding account info.

```

#!/usr/bin/perl

# beginning of configuration

# pop3 host
$pop_host = "pop3.live.com";

# pop3 username 
$pop_user = "user";

# pop3 password
$pop_pass = "pass";

# ssl port number
$ssl_port = "995";

# ssl protocol
$ssl_prot = "tcp";

# number of emails to show
$dis_numb = "5";

# end of configuration def. POP3Client

use Mail::POP3Client;
use IO::Socket::SSL;

  my $socket = IO::Socket::SSL->new( PeerAddr => $pop_host,
                                     PeerPort => $ssl_port,
                                     Proto    => $ssl_prot);
  my $pop = Mail::POP3Client->new();
  $pop->User($pop_user);
  $pop->Pass($pop_pass);
  $pop->Socket($socket);
  $pop->Connect();

$msg_count = $pop->Count();

for ($i = $msg_count, $j = 0; $i >= $msg_count-($dis_numb-1); $i--, $j++) {
  foreach ( $pop->Head( $i ) ) {
    #/^(From|Subject):\s+/i and print $_, "\n";
    if ($_ =~ m/^From:/) {
      ($from) = ($_ =~ m#^From: .*<(.*)>#);
      $from = substr($from, 0, 30);
      $out .= "$j = $from\n";
    }
  }
  #chop $out;
  `echo -e "$out"> ~/.gmail/.gmail_top`;
}

$pop->Close();

```

i tried the linked thread but it contains nothing conky related 

Thanks, nick

---

### Post by majiren on 2010-02-12
I had same problem, because the perl module is needed to install it type:
```
cpan -i Mail::POP3Client
```

---

