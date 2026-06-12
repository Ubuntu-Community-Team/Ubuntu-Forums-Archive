---
title: "Simple Flash/PHP email script question"
date: 2010-08-21
forum: Programming Talk
---

### Post by lazypeterson on 2010-08-21
Alright, I'm trying to get this to work. I know my school's server can do PHP so I'm not sure why this is a problem. Here are the three sets of code: the flash, send_email.php, and send_email_auto_response.php respectively. Any advice would be greatly appreciated!

```
contact_name.text = contact_email.text = contact_subject.text = 
contact_message.text = message_status.text = "";

send_button.addEventListener(MouseEvent.CLICK, submit);
reset_button.addEventListener(MouseEvent.CLICK, reset);

var timer:Timer;
var var_load:URLLoader = new URLLoader;
var URL_request:URLRequest = new URLRequest( "send_email.php" );
URL_request.method = URLRequestMethod.POST;

function submit(e:MouseEvent):void
{
	if( contact_name.text == "" || contact_email.text == "" ||
		contact_subject.text == "" || contact_message.text == "" )
	{
		message_status.text = "Please fill up all text fields.";
	}
	else if( !validate_email(contact_email.text) )
	{
		message_status.text = "Please enter the valid email address.";
	}
	else
	{
		message_status.text = "sending...";
		
		var email_data:String = "name=" + contact_name.text
					   + "&email=" + contact_email.text
					   + "&subject=" + contact_subject.text
					   + "&message=" + contact_message.text;
					   
		var URL_vars:URLVariables = new URLVariables(email_data);
		URL_vars.dataFormat = URLLoaderDataFormat.TEXT;
		
		URL_request.data = URL_vars;
		var_load.load( URL_request );
		var_load.addEventListener(Event.COMPLETE, receive_response );
	}
}

function reset(e:MouseEvent):void
{
	contact_name.text = contact_email.text = contact_subject.text = 
	contact_message.text = message_status.text = "";
}

function validate_email(s:String):Boolean 
{
	var p:RegExp = /(\w|[_.\-])+@((\w|-)+\.)+\w{2,4}+/;
	var r:Object = p.exec(s);
	if( r == null ) 
	{
		return false;
	}
	return true;
}

function receive_response(e:Event):void
{
	var loader:URLLoader = URLLoader(e.target);
    var email_status = new URLVariables(loader.data).success;
	
	if( email_status == "yes" )
	{
		message_status.text = "Success! Your message was sent.";
		timer = new Timer(500);
		timer.addEventListener(TimerEvent.TIMER, on_timer);
		timer.start();
	}
	else
	{
		message_status.text = "Failed! Your message cannot sent.";
	}
}

function on_timer(te:TimerEvent):void 
{
	if( timer.currentCount >= 10 )
	{
		contact_name.text = contact_email.text = contact_subject.text = 
		contact_message.text = message_status.text = "";
		timer.removeEventListener(TimerEvent.TIMER, on_timer);
	}
}
```

```

<?php
$contact_name = $_POST['name'];
$contact_email = $_POST['email'];
$contact_subject = $_POST['subject'];
$contact_message = $_POST['message'];

if( $contact_name == true )
{
	$sender = $contact_email;
	$receiver = "tadbingsley@yahoo.com";
	$client_ip = $_SERVER['REMOTE_ADDR'];
	$email_body = "Name: $contact_name \nEmail: $sender \n\nSubject: $contact_subject \n\nMessage: \n\n$contact_message \n\nIP: $client_ip \n\nFlash Contact Form provided by http://www.flashmo.com";		
	$extra = "From: $sender\r\n" . "Reply-To: $sender \r\n" . "X-Mailer: PHP/" . phpversion();

	if( mail( $receiver, "Flash Contact Form - $contact_subject", $email_body, $extra ) ) 
	{
		echo "success=yes";
	}
	else
	{
		echo "success=no";
	}
}
?>
```
```

<?php
$contact_name = $_POST['name'];
$contact_email = $_POST['email'];
$contact_subject = $_POST['subject'];
$contact_message = $_POST['message'];

if( $contact_name == true )
{
	$sender = $contact_email;
	$receiver = "tadbingsley@yahoo.com";
	$client_ip = $_SERVER['REMOTE_ADDR'];
	
	$email_body = "Name: $contact_name \nEmail: $sender \n\nSubject: $contact_subject \n\nMessage: \n\n$contact_message \n\nIP: $client_ip \n\nFlash Contact Form provided by http://www.flashmo.com";
	$email_body_auto_reply = "Hello $contact_name, \nThis is the auto reply message. Thank you. \n\nAdmin - http://www.flashmo.com";
	
	$extra = "From: $sender\r\n" . "Reply-To: $sender \r\n" . "X-Mailer: PHP/" . phpversion();
	$extra_auto_reply = "From: $receiver\r\n" . "Reply-To: $receiver \r\n" . "X-Mailer: PHP/" . phpversion();
	
	mail( $sender, "Auto Reply - Re: $contact_subject", $email_body_auto_reply, $extra_auto_reply );	// auto reply mail to sender

	if( mail( $receiver, "Flash Contact Form - $contact_subject", $email_body, $extra ) )
	{
		echo "success=yes";
	}
	else
	{
		echo "success=no";
	}
}
?>
```

---

### Post by shadylookin on 2010-08-22
Where exactly in this process are you having problems? Does the flash ever call the php file?



I'm no authority on flash by any means, but 

var_load.load( URL_request );
var_load.addEventListener(Event.COMPLETE, receive_response );

I'm pretty sure you should register your event listener before you start trying to load. 

Are you sure 

var email_status = new URLVariables(loader.data).success;

is the proper way to retrieve that string?

Whenever I've sent request and expected results I would use

var result:String = event.target.data;

which in your case result would then be set to success=yes

and then you could check to see if result == "success=yes"

If you're sure the way you have it is valid then by all means ignore this advice

---

