---
title: "Perl - Net::XMPP library question"
date: 2010-11-28
forum: Programming Talk
---

### Post by rampageoberon on 2010-11-28
Hi,

I'm trying to write a jabber client using perl and the Net::XMPP library.

Just wondering how I can get it to connect two clients within the script? If I try use the below code loop, it only does so for the first client, client1.

I need two clients within the same script as I need it to relay messages between two different jabber servers. So can't create two different scripts for the two clients.

```
$client1->Execute(hostname=>$hostname1,port=>$port1,username=>$username1,password=>$password1,resource=>$resource1);
$client2->Execute(hostname=>$hostname1,port=>$port2,username=>$username2,password=>$password2,resource=>$resource2);
```

Thanks,

---

### Post by gmargo on 2010-11-28
Maybe you need to use $hostname2 instead of $hostname1 for $client2?

---

### Post by rampageoberon on 2010-11-28
Sorry, thats a typo from my end ... and corrected now. I still can't get it to do both connections, it only executes the first one, client1, to start the loop.

---

### Post by gmargo on 2010-11-28
Can you cut your code down to an ultra-minimal (yet complete) example that demonstrates the problem? Please don't make us reinvent your wheel.

---

### Post by rampageoberon on 2010-11-29
Thanks for your reply. Below is the code which should demonstrate what I want to achieve. I basically want to have the clients relaying messages between 2 different jabber servers.

```
#!/usr/bin/perl

use strict;
use warnings;
use Net::XMPP;

#---Set config
my $hostname1 = '';
my $port1 = '';
my $username1 = '';
my $password1 = '';
my $resource1 = '';
my $domain1 = '';
my $chatroom = '';
my $hostname2 = '';
my $port2 = '';
my $username2 = '';
my $password2 = '';
my $resource2 = '';
my $domain2 = '';
my $user = '';

#---Define the clients
my $client1 = new Net::XMPP::Client();
my $client2 = new Net::XMPP::Client();

#---Define callbacks
$client1->SetCallBacks(onauth=>\&send_1_status);
$client1->SetMessageCallBacks(groupchat=>\&chat1);
$client2->SetCallBacks(onauth=>\&send_2_status);
$client2->SetMessageCallBacks(chat=>\&chat2);

#---Connect clients
$client1->Execute(hostname=>$hostname1,port=>$port1,username=>$username1,password=>$password1,resource=>$resource1);
$client2->Execute(hostname=>$hostname2,port=>$port2,username=>$username2,password=>$password2,resource=>$resource2);


#---Send client1 online state
sub send_1_status
{
	$client1->PresenceSend(show=>"available");
	$client1->PresenceSend(to=>$chatroom."\@conference.".$domain1."/".$username1,show=>"available");
}
#---Send client2 online state
sub send_2_status
{
	$client2->PresenceSend(show=>"available");
}

#---Messages received by client2 - sent to chatroom by client1
sub chat2
{
	my ($sid2,$msg2) = @_;
	my $cmd2 = $msg2->GetBody();
        $user = $msg2->GetFrom();

	if ($cmd2 ne "")
	{
$client1->MessageSend(to=>$chatroom."\@conference.".$domain1,body=>$cmd2,type=>"groupchat");
	}
}

#---Relay chat from chatroom back to client2
sub chat1
{
	my ($sid1,$msg1) = @_;
	my $cmd1 = $msg1->GetBody();

	if ($cmd1 ne "")
	{
$client2->MessageSend(to=>$user."\@".$domain2,subject=>"",body=>$cmd1,type=>"chat");
	}
}

```

---

### Post by gmargo on 2010-11-29
Your code does not compile.  However, the basic flaw is the use of the **Execute()** method.  As near as I can tell, Execute() does not return - it sets everything up and then loops on the **Process()** method for as long as the connection exists.  Have a look at the Execute() source in /usr/share/perl5/Net/XMPP/Connection.pm.

You'll probably have to set up each connection with Connect() and then do your own loop to call both client's Process() methods.

---

### Post by rampageoberon on 2010-11-29
Thanks again for the help and assistance. I appreciate this. I'd made some silly mistakes and typo's in stripping down the code. I've corrected it all and edited the earlier post.

And yes, I'm using Execute() to loop on the Process() method.

---

