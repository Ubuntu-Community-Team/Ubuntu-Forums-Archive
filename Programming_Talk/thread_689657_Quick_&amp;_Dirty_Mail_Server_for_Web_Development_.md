---
title: "Quick &amp; Dirty Mail Server for Web Development Testing"
date: 2008-02-06
forum: Programming Talk
---

### Post by SuperMike on 2008-02-06
If you're doing web development testing and need to bring up a quick and dirty local POP/IMAP/SMTP mail server on Ubuntu, here's what I figured out. Following these instructions, **you can bring up a working local mail server on Ubuntu in under 1 minute**. It's not 100% secure like other mail servers, and it's with an unsupported product, but hey, it's great for testing your web applications out as a web developer.

sudo apt-get update
sudo apt-get install hula*
sudo hulasetup --domain=localhost
sudo /etc/init.d/hula start

Connect to: [http://localhost:89/](http://localhost:89/) for the web admin interface.
Login is admin/hula.

Create a new user under Context by clicking it and then clicking Create in the bottom right-hand corner. Choose User, then fill in the required fields. Don't create an OU to contain your users because I tried and I don't think it works.

Connect to [http://localhost:8080/](http://localhost:8080/) for the webmail interface. Login as your new user and password. It should load okay. Note the inbox doesn't dynamically refresh and you have to wait a bit on messages and then click Refresh. Takes about 30 seconds for a sent message to appear for some unknown reason.

Your email address is the user ID you created + "@" + hostname. So, if I'm "supermike", and my computer is named "powerful", my email address is "supermike@powerful". Note I don't have a ".com" on the end because I didn't name my computer "powerful.com".

For POP and SMTP connectivity from Thunderbird, note that I couldn't get POP to work, so I used IMAP. Go with anything you want in the Account Wizard except Email Address should be as stated in the last paragraph, like "supermike@powerful", choose IMAP, Incoming Server is localhost, then OK, OK, on everything else. Change your Outgoing SMTP Server to localhost, port 25, set the username to your username for the account you created in Hula (like "supermike"), and check TLS, if available. Click OK, OK, and now you can send and receive email addressed to user@host ("supermike@powerful" in my case). When you read or send messages, the password it wants is the one you created on the user account in Hula.

If you ever need to stop HulaMail, do 'sudo hulastop'. If you need to start it, do 'sudo /etc/init.d/hula start'

Note that this mail server requires SMTP Authentication with that user's user account, so the ordinary PHP mail() function from your code won't work. Instead, if you're handy with base64_encode and SMTP auth and socket communication, you can go that route. Otherwise, you can use phpmailer, PEAR Mailer, or some other kind of mail class on the web.

Enjoy!

---

### Post by SuperMike on 2008-02-10
To add more "virtual domains" (fake domains so that you can test real-looking email addresses rather than sending to you@localhost all the time), just do this:

1. Go into Hula Web Admin:

[http://localhost:89/](http://localhost:89/)

2. Login as admin/hula.

3. Expand Internet Services, then Server Messaging Server, then click on SMTP Agent.

4. In global domains, add your new domain like "test.com".

5. Click Save. Note this won't won't be activated until you reboot or restart the hula service from the instructions below.


And, again, if you haven't created accounts, let's do so:

1. Now expand Context in the treeview, click on it, and choose Create from the button in the right-hand corner of the screen.

2. When a popup shows up, choose User and a form appears for you to create an account.

3. Type in the account information and don't worry about the domain because this account will work with any of the global domains you had created.

4. Now click on each created account under the Context item in the treeview on the left, then choose Internet Messaging tab, then click features, then enable both IMAP and POP and click Save.

5. Click Logout.

6. Open a command terminal and do:

$ sudo su
# hulastop

(wait about 30 seconds...)

# /etc/init.d/hula start

7. So, if I have already created supermike@localhost, I can now send/receive that mail as [email]supermike@test.com[/email]. It's the same inbox as supermike@localhost.

---

### Post by SuperMike on 2008-02-10
If you're into PHP, I wrote a quick and dirty SMTPMailer class (changing one from public domain I found at php.net). You can use this to connect to an SMTP mail server that requires authentication, rather than have to use PHPMailer or PHP::PEAR. Note it doesn't do MIME or HTML EMail, and I'm not certain but think you might have trouble with = signs in the page. So, please test and modify as necessary. Works great for me with plain-text emails, though. (Note that for forced line wraps in the message body I have to pass those wraps as: \r, not \r\n.)

[PHP]<?php 

/*

USAGE

$sServer = 'localhost';
$sDomain = 'localhost';
$sUser = 'myusername';
$sPass = 'mypassword';
$sFromDisplay = 'Mr. User';
$sFrom = 'myusername@powerful';
$sToDisplay = 'Mr. User';
$sTo = 'myusername@powerful';
$sSubject = 'test';
$sBody = "This is my test.";
$mailer->SendMail(
	$sServer, $sDomain, 0, 0, TRUE, $sUser, $sPass,
	$sFromDisplay, $sFrom, $sToDisplay, $sTo, $sSubject, $sBody,
	TRUE, TRUE
);
*/

class ClassOfMailer {

	function SendMail(
		$sServer='localhost', $sDomain='localhost', $nPort, $nTimeout, $bAuth, $sUser, $sPass, 
		$sFromDisplay, $sFrom, $sToDisplay, $sTo, $sSubject, $sBody, 
		$bEchoCommands=False, $bEchoResponses=False
	) {
		$nPort = empty($nPort) || $nPort == '' || $nPort == 0 ? 25 : $nPort;
		$nTimeout = empty($nTimeout) || $nTimeout == '' || $nTimeout == 0 ? 30 : $nTimeout;
		$bAuth = empty($bAuth) || $bAuth == '' ? 0 : 1;
		$sDate = gmdate('r');
		$sMessage = "To: $sToDisplay <$sTo>\r\nFrom: $sFromDisplay <$sFrom>\r\nDate: $sDate\r\nSubject: $sSubject\r\n\r\n$sBody";
		$hMail = $this->_SMTPConnect($sServer, $nPort, $nTimeout, $bEchoCommands, $bEchoResponses);
		$this->_SMTPWrite($hMail, "EHLO $sDomain\r\n", $bEchoCommands);
		sleep(1);
		if ($bAuth) {
			$this->_SMTPWrite($hMail, "AUTH LOGIN\r\n", $bEchoCommands);
			$this->_SMTPWrite($hMail, base64_encode($sUser) . "\r\n", $bEchoCommands);
			$this->_SMTPWrite($hMail, base64_encode($sPass) . "\r\n", $bEchoCommands);
			sleep(1);
		}
		$this->_SMTPWrite($hMail, "MAIL FROM:<$sFrom>\r\n", $bEchoCommands);
		$this->_SMTPWrite($hMail, "RCPT TO:<$sTo>\r\n", $bEchoCommands);
		$this->_SMTPWrite($hMail, "DATA\r\n", $bEchoCommands);
		$this->_SMTPWrite($hMail, "$sMessage\r\n.\r\n", $bEchoCommands);
		$this->_SMTPWrite($hMail, "QUIT\r\n", $bEchoCommands);
		$this->_SMTPClose($hMail);
	}
	   
	private function _SMTPConnect($sHost, $nPort, $nTimeout=30, $bEchoCommands=False, $bEchoResponses=False) {
		$nErr = 0;
		$sErr = 0;
		if ($bEchoCommands) {
			echo "CONNECTING TO $sHost\r\n"; 
		}
		$hMail = fsockopen($sHost, $nPort, $nErr, $sErr, $nTimeout);
		if (!$hMail) {
			if ($bEchoCommands) {
				echo "CONNECTION FAILED\r\n"; 
			}
			return False;
		}
		if ($bEchoCommands) {
			echo "SUCCESS\r\n"; 
		}
	    $sResponse = fgets($hMail,1);
	    $nBytesLeft = socket_get_status($hMail);
	    if ($nBytesLeft > 0) { 
			$sResponse .= @ fread($hMail, 1024);
		}
		if ($bEchoResponses) {
			echo $sResponse; 
		}
		return $hMail;
	}
	
	private function _SMTPWrite($hMail, $sCommand, $bEchoCommands=False) {
		if ($bEchoCommands) {
			echo $sCommand; 
		}
		fputs($hMail, $sCommand);
		$sResponse = fgets($hMail,1);
		$nBytesLeft = socket_get_status($hMail);
		if ($nBytesLeft > 0) { 
			$sResponse .= @ fread($hMail, 1024);
		}
		return $sResponse; 
	}
	   
	private function _SMTPClose($hMail) {
	    fclose($hMail);
	}
	
}

// THIS INSTANTIATES THE CLASS SIMPLY BY INCLUDING THE SCRIPT
$mailer =& new ClassOfMailer();

	
?>[/PHP]

---

### Post by SuperMike on 2008-02-26
You may have trouble with getting Hula installed on Gutsy Ubuntu. I did. The fix is to replace 'gutsy' with 'feisty' in /etc/apt/sources.list, perform 'sudo apt-get update', perform 'sudo apt-get install hula', switch your apt sources back to 'gutsy', perform 'sudo apt-get update' again, and then move on with the hula setup that I have mentioned previously in this thread.

Note I said 'apt-get install hula', not 'apt-get install hula*'. The latter option will give you an error about a C library, whereas the former will just work.

And don't forget to switch your apt sources back to gutsy when done!

---

### Post by daniel83 on 2010-05-04
I'm using Hardy, seemed to install ok, but when I run 
sudo hulasetup --domain=localhost
I get hulasetup not found.

When it comes to Linux I only know how to copy and paste commands. (and that's all I'm happy with for now).

Cheers,
Daniel.

---

