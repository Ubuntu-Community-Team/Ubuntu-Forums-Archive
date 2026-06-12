---
title: "Attempt at php irc bot..."
date: 2007-05-28
forum: Programming Talk
---

### Post by Znupi on 2007-05-28
I'm trying to make an IRC bot, in PHP. I've searched for protocol documentation, and came across [http://www.ucc.asn.au/~matt/mirror/irctelnet.html](http://www.ucc.asn.au/~matt/mirror/irctelnet.html) because I am too lazy to read the RFC (c'mon, it's way too big). The only problem is, I don't think that site is right. I try to send the "user" command but it seems it's not working, I get nothing back and if I try to join a channel, I get an error saying I need to login/register. I get no PING messages to which to respond with PONG, but I get disconnected because of timeout.

Help? Also, I made this little program in php, expecting it to at least stay connected, but it doesn't :(. Anyone who knows the IRC protocol? Any (short) docs on it? I don't feel like reading the RFC, it's huge.

```

#!/opt/lampp/bin/php-5.2.1

<?php

set_time_limit(0);

class PhpIrc {
	function __construct($srv, $port, $nick) {
		$this->srv = $srv; $this->nick = $nick;
		$this->socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
		socket_connect($this->socket, $srv, $port);
		$str = "user {$nick} znupi.sytes.net {$srv} :PhpIrcPinger";
		socket_send($this->socket, $str, strlen($str), 0);
		echo "<< {$str}\n";
		$str = '';
		$this->msgLoop();
	}
	function msgLoop() {
		while ( ($buf = socket_read($this->socket, 2048)) !==false ) {
			if (!$buf) continue;
			echo ">> {$buf}\n";
			$words = explode(" ", $buf);
			switch($words[0]) {
				case "ping":
					$str = "pong {$words[1]}";
					break;
			}
			if ($str) {
				socket_send($this->socket, $str, strlen($str), 0);
				echo "<< {$str}\n";
				$str = '';
			}
		}
	}
}

$test = new PhpIrc($argv[1], $argv[2], $argv[3]);

?>

```
But all I get is:
```

$ ./irc.php irc.undernet.org 6667 Znupi

<< user Znupi znupi.sytes.net irc.undernet.org :PhpIrcPinger
>> NOTICE AUTH :*** Looking up your hostname

>> NOTICE AUTH :*** Checking Ident

>> NOTICE AUTH :*** No ident response

>> NOTICE AUTH :*** Couldn't look up your hostname

>> ERROR :Closing Link:  by LosAngeles.CA.US.Undernet.org (Registration Timeout)

```

---

### Post by theY4Kman on 2008-07-30
I'm having the exact same problem. My bot used to connect, but now it displays what yours outputs. I was kind of disappointed when there were no replies to this thread.

---

### Post by jinksys on 2008-08-14
Wow, there is hardly any information on that page.

---

### Post by Znupi on 2008-08-22
Sorry for bumping an uber-old thread, but I've had another shot at it and it works. Btw search Google for "irc telnet" and you'll get a lot of good results. I also read a few bits from the RFC :D. Here's my bot:
```

<?php

/**
 * @author Felix Oghina
 * @desc A bot that connects to an IRC server and joins a particular channel. This is the main class that handles the connection.
 * @version 0.0.2
 * @copyright 2008 Felix OGhina
 */
class PhpIrc {
	
	var $_NAME_ = "PhpIrc Bot";
	var $_VERSION_ = "0.0.2";
	var $_DEBUG_ = true;
	
	var $C = Array (
		'RPL_ENDOFMOTD' => 376
	);
	
	/**
	 * @desc Class constructor. This connects to the server and logs in.
	 * @param $hostname Hostname of the server to connect to.
	 * @param $channel The channel to join.
	 * @param $nickname The nickname to use.
	 * @param $port Optional argument specifying the port on which to connect. Defaults to 6667.
	*/
	function __construct($hostname, $channel, $nickname, $port = 6667) {
		
		// Set time limit to be infinite.
		set_time_limit(0);
		// This makes php fill the $php_errormsg var with the last php error.
		if (!ini_get('track_errors')) ini_set('track_errors', true);
		
		// Save the arguments so they can be used by other functions, too.
		$this->hostname = $hostname;
		$this->channel  = $channel;
		$this->nickname = $nickname;
		$this->port     = $port;
		
		// Connect to the server.
		$this->fpSocket = @fsockopen($hostname, $port, $errno, $errstr, 10);
		if (!$this->fpSocket) {
			trigger_error("[" . __METHOD__ . "] Error #{$errno}: {$errstr}", E_USER_WARNING);
			return;
		}
		// Make the socket blocking and set the read/write timeout to 10 seconds.
		stream_set_blocking($this->fpSocket, true);
		stream_set_timeout($this->fpSocket, 10);
		
		// Get machine's hostname (UNIX only)
		$local_hostname = trim(@file_get_contents("/etc/hostname"));
		if (!$local_hostname) $local_hostname = "localhost"; // Non-UNIX OSes
		
		// Log in.
		$this->send("NICK {$nickname}");
		$this->send("USER {$nickname} {$local_hostname} {$hostname} :{$this->_NAME_} {$this->_VERSION_}");
		
		// Start the message receive / send loop..
		$this->message_loop();
		
	}
	
	/**
	 * @desc Receives messages from the server and responds to them by case.
	 */
	function message_loop() {
		
		$cmd = '';
		while (!feof($this->fpSocket)) {
			
			// Read data from socket.
			$buf = @fread($this->fpSocket, 1024);
			if ($buf === false) trigger_error("[" . __METHOD__ . "] Error: {$php_errormsg}\nWhile reading from socket.", E_USER_WARNING);
			$cmd .= $buf;
			if (strpos($cmd, "\n") === false) continue;
			$cmd_array = explode("\n", substr($cmd, 0, strrpos($cmd, "\n")));
			$cmd = substr($cmd, strrpos($cmd, "\n")+1);
			
			// Parse received commands
			foreach($cmd_array as $cur_cmd) {
				if ($this->_DEBUG_) echo '>> ' . $cur_cmd . "\n";
				$cmd_args = explode(" ", $cur_cmd);
				$num = intval($cmd_args[1]);
				
				// Numeric reply
				if ($cur_cmd[0] == ':' && $num) {
					switch ($num) {
						case $this->C['RPL_ENDOFMOTD']:
							$this->send("JOIN {$this->channel}");
							break;
					}
				}
				
				// Non-numeric command
				else {
					$switch_by = ($cur_cmd[0] == ':') ? $cmd_args[1] : $cmd_args[0];
					switch ($switch_by) {
						case "PING":
							$this->send("PONG {$cmd_args[1]}");
							break;
						case "PRIVMSG":
							unset($cmd_args[0], $cmd_args[1], $cmd_args[2]);
							$msg = trim(substr(implode(" ", $cmd_args), 1));
							if ($msg == $this->nickname) $this->send_message("What?");
							else if ($msg == "talk") $this->send_message("What do you want me to tell you?");
							else if ($msg == "about you") $this->send_message("I'm {$this->_NAME_} v{$this->_VERSION_}. Nice to meet you.");
							else if ($msg == "bye bye") {
								$this->send_message("I shall go now. I have to.. uhm... compile something..");
								$this->send("QUIT :Compile error!");
							}
							break;
						case "ERROR":
							if ($cmd_args[1] . $cmd_args[2] == ":Closing Link:") break 3;
							break;
					}
				}
			}
		
		}
		
		// Close socket
		fclose($this->fpSocket);
	}
	
	/**
	 * @desc Send a command to the IRC Server.
	 * @param $string The command to send.
	*/
	function send($string) {
		
		// Append a newline character to the string because that's how IRC commands are formed.
		$command = $string . "\n";
		$bytes = @fwrite($this->fpSocket, $command);
		if ($bytes === false) trigger_error("[" . __METHOD__ . "] Error: {$php_errormsg}\nWhile sending command: {$string}", E_USER_WARNING);
		// If we're debugging, output the sent command.
		if ($this->_DEBUG_) echo '<< ' . $command;
		
	}
	
	/**
	 * @desc Send a message to the channel.
	 * @param $string The message to send.
	 */
	 function send_message($string) {
	 	
	 	$this->send("PRIVMSG {$this->channel} :{$string}");
	 	
	 }
	 
}

?>

```
Here's what it does so far:
```

16:03:34 -- SmartBot (~SmartBot@204-37-GZA-1mai.titannet.ro) has joined #Znupi
16:03:48 -- User SmartBot: ~SmartBot@204-37-GZA-1mai.titannet.ro - PhpIrc Bot 0.0.2
16:03:48 -- User SmartBot: on channels #Znupi 
16:03:48 -- User SmartBot: on server punch.va.us.dal.net ( 'The moon, of course!' Nasrudin replied. )
16:04:07 <Znupi> SmartBot
16:04:07 <SmartBot> What?
16:04:10 <Znupi> talk
16:04:10 <SmartBot> What do you want me to tell you?
16:04:13 <Znupi> about you
16:04:13 <SmartBot> I'm PhpIrc Bot v0.0.2. Nice to meet you.
16:04:17 <Znupi> bye bye
16:04:17 <SmartBot> I shall go now. I have to.. uhm... compile something..
16:04:18 -- SmartBot has quit (Quit: Compile error!)

```
Enjoy ^.^

---

### Post by theperson10 on 2009-04-24
Apologies for the bump, but i thought i'd share a change I made, and see if maybe you guys could do it better than I

What i did was for the express purpose of allowing the bot to interact in multiple channels

Here's the diff:
```
--- wyre.inc.old.php	2009-04-23 21:28:44.000000000 -0700
+++ wyre.inc.php	2009-04-23 21:49:28.000000000 -0700
@@ -19,7 +19,7 @@
 	/**
 	 * @desc Class constructor. This connects to the server and logs in.
 	 * @param $hostname Hostname of the server to connect to.
-	 * @param $channel The channel to join.
+	 * @param $channel an array of channels to join.
 	 * @param $nickname The nickname to use.
 	 * @param $port Optional argument specifying the port on which to connect. Defaults to 6667.
 	*/
@@ -85,7 +85,9 @@
 				if ($cur_cmd[0] == ':' && $num) {
 					switch ($num) {
 						case $this->C['RPL_ENDOFMOTD']:
-							$this->send("JOIN {$this->channel}");
+							foreach ($this->channel as $value){
+								$this->send("JOIN {$value}");
+							}
 							break;
 					}
 				}
@@ -98,13 +100,14 @@
 							$this->send("PONG {$cmd_args[1]}");
 							break;
 						case "PRIVMSG":
+							$to_chan = $cmd_args[2];
 							unset($cmd_args[0], $cmd_args[1], $cmd_args[2]);
 							$msg = trim(substr(implode(" ", $cmd_args), 1));
-							if ($msg == $this->nickname) $this->send_message("What?");
-							else if ($msg == "talk") $this->send_message("What do you want me to tell you?");
-							else if ($msg == "about you") $this->send_message("I'm {$this->_NAME_} v{$this->_VERSION_}. Nice to meet you.");
+							if ($msg == $this->nickname) $this->send_message("What?", $to_chan);
+							else if ($msg == "talk") $this->send_message("What do you want me to tell you?", $to_chan);
+							else if ($msg == "about you") $this->send_message("I'm {$this->_NAME_} v{$this->_VERSION_}. Nice to meet you.", $to_chan);
 							else if ($msg == "bye bye") {
-								$this->send_message("I shall go now. I have to.. uhm... compile something..");
+								$this->send_message("I shall go now. I have to.. uhm... compile something..", $to_chan);
 								$this->send("QUIT :Compile error!");
 							}
 							break;
@@ -139,13 +142,24 @@
 	/**
 	 * @desc Send a message to the channel.
 	 * @param $string The message to send.
+	 * @param $target the channel to send the message to.
 	 */
-	 function send_message($string) {
+	 function send_message($string, $target) {
 	 	
-	 	$this->send("PRIVMSG {$this->channel} :{$string}");
+	 	$this->send("PRIVMSG {$target} :{$string}");
 	 	
 	 }
 	 
+	/**
+	 * @desc Send a message to all channels the bot is in.
+	 * @param $string The message to send.
+	 */
+	 function send_global_message($string) {
+	 	foreach ($this->channel as $value){
+			$this->send("PRIVMSG {$value} :{$string}");
+		}
+	 }
+	 
 }
 
 ?>

```
Whatcha think?

---

