---
title: "PHP question about CURL???"
date: 2011-06-30
forum: Programming Talk
---

### Post by hockey97 on 2011-06-30
hi, I am trying to use a  api from some company.

The protocol is https that it uses.

I need to send commands to a url via post method.

I then am supposed to get data sent back via XML or PHP serialization. It must be specified via the commands.

I am not 100% sure but the api is supposed to give me a list of data. So I assume it's in an array form being sent back.

I need to make a html form. This form will have a ajax effect.

so first I will grab data from the api and then insert it inside the select tags which are drop down menus.

then when the button is submitted I want to send all data to the api again to submit data.


Is there any tutorials that teaches how to send data to the url and then capture or get the response back and then display it or put it inside a variable?

---

### Post by zobayer1 on 2011-06-30
You can just google it. PHP cURL form POST submit.
For https usage, you have to set appropriate curl_opt options. when you execute curl, it will also grab the return data, and error code.

---

### Post by hockey97 on 2011-06-30
> **zobayer1 said:**
> You can just google it. PHP cURL form POST submit.
For https usage, you have to set appropriate curl_opt options. when you execute curl, it will also grab the return data, and error code.

I have, but the tutorials I found only shows how to post the form to a remote server.

they give the example in http only and do say if you need to use https you just do the same thing as http but replace the url instead of http you put https. Then they said you will have to set the https protocal option to true. 

but they don't show example code of it.

I also want to know how you can receive the data. I haven't found a tutorial or example code showing how to receive the data requested. 

Also if the response gives an array of information would be sent as an array?


my guess would be for example:

$data = curl_exec();

that $data variable will hold the response that is given back from the api of that remote server.

---

### Post by zobayer1 on 2011-07-01
> **hockey97 said:**
> I have, but the tutorials I found only shows how to post the form to a remote server.

they give the example in http only and do say if you need to use https you just do the same thing as http but replace the url instead of http you put https. Then they said you will have to set the https protocal option to true. 

but they don't show example code of it.

I also want to know how you can receive the data. I haven't found a tutorial or example code showing how to receive the data requested. 

Also if the response gives an array of information would be sent as an array?


my guess would be for example:

$data = curl_exec();

that $data variable will hold the response that is given back from the api of that remote server.

more clearly, if you send some data to thispage.php, for example, $data will hold the resulting page as that you would get when you would try it from a browser.
[http://ubuntuforums.org/showthread.php?t=1783019](http://ubuntuforums.org/showthread.php?t=1783019)
This is a thread related to cURL, the 2nd page contains talks about https and the first page has a simple application.
I have never tried https before.

---

### Post by hockey97 on 2011-07-01
Thanks for the reply. I looked at that page. I think I understand the https way to do the things.

I looked at many curl tutorials on google. I can't find an example of how to receive an array of data via php serialization.  

The api I am using will send data back. It be in an array form.

here is my code 

[php]
$ch = curl_init("https://api.servers.com/?"); 
curl_setopt($ch, CURLOPT_HEADER, 1); 
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1); 
curl_setopt($ch, CURLOPT_POST, 1); 
$maple="&auth_username=user&auth_password=pass&section=domain&command=info&return_type=serialization";
curl_setopt($ch, CURLOPT_POSTFIELDS, $maple);
curl_setopt ($ch, CURLOPT_SSL_VERIFYPEER, 1); 
curl_setopt ($ch, CURLOPT_SSL_VERIFYHOST, 2);
$data = curl_exec($ch); 
$tingy= unserialize($data);
curl_close($ch);
[/php]

the user name and password I writte directly but replaced with user and pass for security issues. So just think that the user be thereal username and it's not a variable. I have it directly type there.

I then echo $tingy. that variable be the content. It should have a list of product names in an array.

I am not sure if $tingy should be $tingy[0]  to make it an array.

---

### Post by zobayer1 on 2011-07-01
To print array, you can use print_r function. What do you get when you do that?

You have said that after successful login, your target will send an array of information to you, which form will it be? POST? or GET? I think to receive the data, you could simply use $_POST variable? Or it is something else?

---

