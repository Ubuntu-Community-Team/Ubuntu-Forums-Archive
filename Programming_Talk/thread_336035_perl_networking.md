---
title: "perl networking"
date: 2007-01-11
forum: Programming Talk
---

### Post by spx3 on 2007-01-11
i've read this [http://www.perlfect.com/articles/sockets.shtml](http://www.perlfect.com/articles/sockets.shtml)
and found it to be a very good introduction to network programming in perl
but my problem is that what is there is not enough.
as one can see,it only permits communication in one sense and not the
other.
i've tried to improvise on what i saw there and try to make it the other
way around also.
i've succeded somehow,but it works only for...about 3 seconds and then
i think it stops.
i need help on this,i must say that i have checked a book
Network Programming in Perl and also some other articles and was not
able to found a solution.

Ok,now the code,and afterwards some comments about it.


receiver.pl
```

use IO::Socket;
my $sock = new IO::Socket::INET (
	LocalHost => 'localhost',
	LocalPort => '7070',
	Proto=>'tcp',
	Listen=>1,
	Reuse=>1,
);
my $new_sock = $sock->accept();
$i=0;

while(1){
print $new_sock "HIII CALLER!\n";
print $new_sock "stop reading ,caller!\n";
while(<$new_sock>){
	print $_;
	if($_ == "stop reading ,receiver!\n"){
		last;
	};
}
}
close($sock);

```



caller.pl
```

use IO::Socket;
$sock =0;
while(!$sock){
	$sock = new IO::Socket::INET (
	PeerAddr => 'localhost',
	PeerPort => '7070',
	Proto => 'tcp',
);
}
die "Could not create socket: $!\n" unless $sock;

while(1){
print $sock "HIIII RECEIVER!\n";
print $sock "stop reading ,receiver!\n";
while(<$sock>){
	print $_;
	if($_ == "stop reading ,caller!\n"){
		last;
	};
}
};
close($sock);

```


in caller.pl we have the first while wich is waiting for receiver to
create the socket,and when the socket will be created
!$sock will be true thus,it will exit the loop and start
writing to the socket and reading from it.
what it will do ,actually is,it will first write a message to the
receiver,and then write a message that the receiver will interpret
as to stop reading and do something else(receiver will write to
the socket his message).
and so forth,and in the end close the socket.

in receiver.pl we create the socket and we start writing and reading from
it,writing some messages to caller and reading what caller has said,
but also interpret the "stop reading receiver!\n" message wich will
mean the receiver will stop reading and will start writing some messages
to caller,but in turn he will also issue a message to caller for him to stop
reading ,the message for this will be "stop reading caller!\n".


what i want you to know is that i do not intend to say that this code is
very correct or anything ,i just want to make it work properly ,that is all.
if you know of any other methods,please inform me.

my questiones are
1)why are both scripts pausing after 3-4 seconds?
2)how can i debug the program ?
3)what other way could i choose to do what i am
  trying to do ?

thank you

---

### Post by yaaarrrgg on 2007-01-11
I had problems getting that example to work the way I wanted.... not sure the <$socket> read is doing things intuitively.  I found a better example at:

[http://evolt.org/node/60108](http://evolt.org/node/60108)

which uses the send and recv methods on the socket.

for example, the server might look like:

```

use IO::Socket::INET;
print ">> Server Program <<\n";

# Create a new socket
$MySocket=new IO::Socket::INET->new(LocalPort=>1234,Proto=>'udp');

$flags = 128;

# Keep receiving messages from client
$def_msg="\nReceiving message from client.....\n";
while(1)
{

    # get message from client
    $MySocket->recv($text,$flags);
    if($text ne '')
    {
        print "\nReceived message '", $text,"'\n";
        $MySocket->send(" *** this is a message from the server *** \n");
    }
    # If client message is empty exit
    else
    {
        print "Cilent has exited!";
        exit 1;
    }
}

```

and the client might look like:

```

# Client Program
use IO::Socket::INET;
print ">> Client Program <<";

# Create a new socket
$MySocket=new IO::Socket::INET->new(PeerPort=>1234,Proto=>'udp',PeerAddr=>'localhost');

$flags = 128;

# Send messages
$def_msg="Enter message to send to server : ";
print "\n",$def_msg;
while($msg=<STDIN>)
{
    chomp $msg;
    if($msg ne '')
    {
        print "\nSending message '",$msg,"'";
        if($MySocket->send($msg))
        {
            print ".....<done>","\n";

            # read a message back from server
            $MySocket->recv($msg, $flags);
            print $msg;

            # prompt again
            print $def_msg;

        }

    }
    else
    {
        # Send an empty message to server and exit
        $MySocket->send('');
        exit 1;
    }
}

```

---

