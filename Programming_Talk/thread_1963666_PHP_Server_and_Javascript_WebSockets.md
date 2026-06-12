---
title: "PHP Server and Javascript WebSockets"
date: 2012-04-22
forum: Programming Talk
---

### Post by JspPeterson on 2012-04-22
Hello. I have created a PHP server and I cannot get it to connect with HTML5 WebSockets. Can someone explain what I am doing wrong?

Server:
[PHP]<?php
$HOST = "localhost";
$PORT = 2000;
//Client Socket Class
class ClientSocket
{
	var $socket;
	var $alive;
	function __construct($sock)
	{
		if($sock)
			$this->socket = $sock;
		else
			$this->socket = socket_create(AF_INET, SOCK_STREAM, 0);
		socket_set_nonblock($this->socket);
		$this->alive = true;
		return $this;
	}
	function isAlive()
	{
		return $this->alive;
	}
	function connect($ip,$port)
	{
		if(socket_connect($this->socket,$ip,$port))
			return true;
		return false;
	}
	function send($data)
	{
		if(socket_write($this->socket,$data))
			return true;
		return false;
	}
	function read($len=1024)
	{
		if(($input = socket_read($this->socket,$len)) === '')
			return "TERMINATED";
		return $input;
	}
	function disconnect()
	{
		socket_shutdown($this->socket);
		socket_close($this->socket);
		$this->alive = false;
	}
}
//Do this when server is already started
set_time_limit(0);
ob_implicit_flush();
function startServer()
{
	global $HOST;
	global $PORT;
	$started = false;
	$socket = socket_create(AF_INET, SOCK_STREAM, 0);
	if($socket === FALSE)
		return false;
	$result = socket_bind($socket, $HOST, $PORT);
	if($result === FALSE)
		return false;
	return $socket;
}
function server_log($line)
{
	$filepath = "./log.html";
	if(!file_exists($filepath))
		server_log_create();
	$file = fopen($filepath,"a+");
	fwrite($file,$line . "\n");
	fclose($file);
}
function server_log_create()
{
	$filepath = "./log.html";
	$file = fopen($filepath,"w+");
	fwrite($file,"
	<html>
	<head>
		<title>PHP Server Log</title>
		<style type='text/css'>
		body
		{
			border:1px solid black;
			background-color:#CCC;
			font-family:lucida console;
			padding:5px;
			overflow-x:hidden;
			overflow-y:auto;
			white-space:pre;
		}
		</style>
	</head>
	<body><h3>--PHP SERVER SOCKET LOG--</h3>");
	fclose($file);
}
//PHP SOCKETING
//socket_read($sock,1024);
//socket_accept($sock);
$server = startServer();
$clients = array();
$clientCount = 0;
if($server === false) //Server either couldn't run, or is already running
{
	$client = socket_create(AF_INET, SOCK_STREAM, 0);
	if(!socket_connect($client,$HOST,$PORT))
		die("Unable to connect.");
	$output = "TALK";
	if($_GET['cmd'])
		$output = $_GET['cmd'];
	socket_write($client,$output);
	$input = socket_read($client,1024);
	print "CLIENT: " . $output . "<br>";
	print "SERVER: " . $input;
}
else //Started the server
{
	server_log("<h2>Server was started.</h2>");
	socket_listen($server,3);
	socket_set_nonblock($server);
	while(true)
	{
		if(($acpt = socket_accept($server)) !== FALSE)
		{
			server_log("Got a connection request.");
			$client = new ClientSocket($acpt);
			array_push($clients,$client);
			$clientCount++;
			server_log("Client connected! [Count: " . $clientCount . "]");
		}
		$i = 0;
		foreach($clients as $client)
		{
			$input = $client->read();
			if($input == "TERMINATED")
			{
				server_log("Client " . $i . " disconnected.");
				unset($clients[array_search($client,$clients)]);
				$clientCount--;
				$client->disconnect();
				$i++;
				continue;
			}
			if(strlen($input))
				server_log("Client " . $i . " input: " . $input);
			if($input == "TERMINATE")
			{
				$client->send("Terminated.");
				$client->disconnect();
				socket_shutdown($server);
				socket_close($server);
				server_log("Server was terminated.");
				die();
			}
			if($input == "TALK")
			{
				$client->send("Hello there.");
			}
			$i++;
		}
		usleep(500000); 
	}
	$client->disconnect();
	server_log("Client was disconnected.");
	socket_shutdown($server);
	socket_close($server);
	server_log("Server was terminated.");
	die();
}[/PHP]

Client:
[HTML]<html>
	<head>
		<title>WS</title>
		<script type="text/javascript" language="javascript">
			function init()
			{
				if(!window.WebSocket)
				{
					document.write("Websockets unavailable.");
					return;
				}
				ws = new WebSocket("ws://hexon.co:2000");
				ws.onopen = function()
				{
					document.write("Opened.");
				}
				ws.onmessage = function()
				{
					document.write("MEssages");
				}
				ws.onclose = function(e)
				{
					console.log(e);
					document.write("closed.");
				}
				ws.onerror = function(e)
				{
					document.write("error " + e);
				}
				document.write("Openning");
			}
			window.addEventListener("load", init, false);
		</script>
	</head>
	<body>
	
	</body>
</html>[/HTML]

---

