---
title: "Marshalling an HTTP POST request using PHP HttpRequest"
date: 2012-10-02
forum: Programming Talk
---

### Post by bluedalmatian on 2012-10-02
Im trying to use PHPs PECL extension HttpRequest class to marshall a form submission using an HTTP post.

Our website has a mailing list hosted by FreeLists and the HTML for the signup form is as follows:

[HTML]
<form action="http://www.freelists.org/cgi-bin/subscription.cgi" method="post">
  			<input type=hidden name="list" value="commstrust">
  			<input type=hidden name="url_or_message" value="">
			<p> Email: <input type="text" name="email"></p>

  			<p>Choose an action:
   			<select name="action">
    				<option value="subscribe">Subscribe</option>
    				<option value="unsubscribe">Unsubscribe</option>
   			</select>
			</p>
 			<button class="submitbutton" type="submit" style="float: right; margin: 3px;">Go</button>
		</form>
[/HTML]
The problem is when the user submits the form the page comes off FreeLists server and is bland and doesnt fit in with our sites look & design, hence what I want to do is alter the action attribute on the form tag to a PHP page on our server which has our sites design look to it, and use PHP to extract the form data use HttpReqeust to forward it to free lists cgi script, then echo out the response into the body of our page.

This is the PHP I have so far:

[PHP]
<?php
					$email=$_POST['email'];
					$action=$_POST['action'];
					$list=$_POST['list'];

					$httpreq=new HttpRequest;

					$httpreq->setUrl('http://www.freelists.org/cgi-bin/subscription.cgi');
					$httpreq->setMethod(HTTP_METH_POST);

					$formfields['email'] = $email;
					$formfields['action'] = $action;
					$formfields['list'] = $list;

					$httpreq->setPostFields($formfields);

					$httpreq->setContentType("application/x-www-form-urlencoded");
					$httpreq->setBody('');


					try 
					{
    						$httpreq->send();
    						if ($httpreq->getResponseCode() == 200) 
   						 {
     							   echo $httpreq->getResponseBody();
   						 }
					} 
					catch (HttpException $ex) 
					{
    						echo 'Sorry an error occurred: ';
    						echo '<br>';
    						echo $ex;
					}

				?>
[/PHP]

But I keep getting the following error:

Sorry an error occurred: 
exception 'HttpInvalidParamException' with message 'Empty or too short HTTP message: ''' in /home/comms/public_html/processfreelistform.phphtml:277 inner exception 'HttpRequestException' with message 'Timeout was reached; connect() timed out! ([http://www.freelists.org/cgi-bin/subscription.cgi](http://www.freelists.org/cgi-bin/subscription.cgi))' in /home/comms/public_html/processfreelistform.phphtml:218 Stack trace: #0 /home/comms/public_html/processfreelistform.phphtml(277): HttpRequest->send() #1 {main}

It looks like Im not setting the header fields properly but I cant fathom out what and Google hasnt turned up any suggestions.

Thanks

---

### Post by Dimarchi on 2012-10-04
Try without

```
$httpreq->setBody('');
```I get the impression that you are trying to send nothing, from the very quick read of HttpRequest documentation ([http://www.php.net/manual/en/httprequest.setbody.php](http://www.php.net/manual/en/httprequest.setbody.php)).

This link might prove to be helpful: [http://www.mkfoster.com/2009/01/04/how-to-use-the-pecl-http-pecl_http-extension-to-make-http-requests-from-php/](http://www.mkfoster.com/2009/01/04/how-to-use-the-pecl-http-pecl_http-extension-to-make-http-requests-from-php/)

Stuff after the install part, that is.

---

