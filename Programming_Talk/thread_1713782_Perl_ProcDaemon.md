---
title: "Perl Proc::Daemon"
date: 2011-03-24
forum: Programming Talk
---

### Post by CryptiniteDemon on 2011-03-24
So I'm trying to get this script to run other programs in the background while also continuing to run.

Basically it's a server that produces new threads for each connection.  There's an API that I use to send text messages, but my only option is to use PHP for that part.  So what I do is call this php script from perl.  I need the php script to run as a daemon.

However, when I try to run the PHP script using Proc::Daemon, it runs the PHP script, but kills the housing perl script.


Code below for example:
```
my $server = new IO::Socket::INET(
			Localhost => "localhost",
			LocalPort => "5555",
			Proto => "tcp",
			Listen => 2,
			Reuse => 1);

while (1)
{
	my $client;
	do
	{
		$client = $server->accept();
	} until ( defined($client) );

	my $thrd = threads->new( \&handleComm, $client,"flf" )->detach();
}



```

So that makes the new thread.  handleComm just parses some strings and then calls functions based on the string. Anyway, it calls the sendAlert function below which calls the php script as a daemon.  However, for some reason, when this command is called it just closes out of the whole server.  

```
sub sendAlert
{
	($xml, $client, $sqlConn) = @_;

	$phone = $xml->{cmdData}->{phone};
	
	my $daemon = Proc::Daemon->new(
        work_dir     => '/opt/theseBins/',
        exec_command => "php -f sendSMS.php $phone",

}
```


what I want is for this to call the PHP script as a daemon without killing the server.

---

### Post by paxxus on 2011-03-24
I happen to be working on a Perl script which spawns a lot of children running in the background.

I have a sub routine which spawns a child process and returns the PID to the parent, i.e. the main Perl script (the server).

```
sub spawn_child
#
# Spawn a child process given by the supplied shell command string.
# Returns the process ID of the child.
#
{
        my $command = shift;
        my $pid = fork();
        die("fork failed") if (not defined $pid);
        return($pid) if ($pid != 0);
        exec($command);
        exit 1;
}
```I then use the waitid() function to do a non-blocking wait on child process completion, e.g.:

```

use POSIX ":sys_wait_h";

my $pid = spawn_child( "sleep 10" );

while ( 1 ) {
  my $id = waitid( $pid, &WNOHANG );
  if ( $id == $pid ) {
    # Child completed, return status in $?
  } else {
    die( "Unknown child process" ) if ( $id != 0 );
    # Child still running.
  }
}
```Not sure if this is what you need, but it works splendidly for my purposes. I believe the children dies if the parent / server dies though, but that doesn't matter in my use case.

---

