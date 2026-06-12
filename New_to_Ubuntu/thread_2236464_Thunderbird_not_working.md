---
title: "Thunderbird not working"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by afrancis-ozonline on 2014-07-27
I have been using Thunderbird for some time without a problem, now when I open the program I receive this message:
"Server not found

live.mozillamessaging.com could not be found. Please check the name and try again.


    Check the address for typing errors such as ww.example.com instead of [www.example.com](www.example.com)
    If you are unable to load any pages, check your computer's network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Thunderbird is permitted to access the Web."

My internet connection is working fine. Can anyone help with this problem?

---

### Post by amanchesterman on 2014-07-27
You may find it helpful to read this thread: [https://support.mozilla.org/en-US/questions/993843](https://support.mozilla.org/en-US/questions/993843). The error message discussed is not the same as yours, but the thread explains that 'live.mozillamessaging.com' is the Thunderbird welcome message that you would normally see when you start the program and it suggests some things you could try.
Your post doesn't say what happens if you simply ignore the warning and proceed: can you receive and send email messages? If so, the problem is simply with your Thunderbird installation.
You could try simply uninstalling and re-installing Thunderbird from scratch, there's at least one post in the Mozilla forum where someone did that and it cured the problem.

---

### Post by afrancis-ozonline on 2014-07-29
I cannot receive emails if I click on "Get Messages" a text comes up at the bottom which shows my email address then "Looked up mail.bigpond.com" and nothing else happens.

---

### Post by amanchesterman on 2014-07-29
Hmm. Well if your internet connection is 'working fine', then I would guess that either (a) Thunderbird is failing to send the correct login and password information to your email provider or (b) your email provider's server is failing to recognise your login information and/or to send the mail to your computer.
Either way, as a first step I would close Thunderbird, open your internet browser (Firefox or whatever) and go to the website of the company that provides your email service. (I don't know which company manages the "bigpond" domain.) It's likely that on that website there is a way to log in to your mail account using a webmail interface -- i.e., using your browser instead of TBird. Make sure that you can log in to your account, check your mails, and send and receive a test message at least.
If you can do that, it will confirm that you have the correct username and password and that there is nothing on the company's website blocking your mail. (It happened to me once that my mail provider had changed the terms and conditions of their service and I had to agree to that through their webmail page: until I did so, my Thunderbird like yours could not receive anything.)
If all is OK using the webmail page, then at least you have a functioning email system until you can sort out Thunderbird. I would suggest you then check very carefully the account information stored in your Thunderbird: username, security settings, names of the incoming and outgoing mail servers, port numbers etc. Also check that you don't have any Thunderbird add-ons that might be creating problems: go to the Thunderbird 'help' menu and choose the option 'restart with add-ons disabled'.

---

### Post by afrancis-ozonline on 2014-07-30
I should have mentioned that although I really like Ubuntu I also look at other versions on Linux as well as Windows. Thunderbird works fine on my versions of Mint and also Windows 7. I have checked the the account information and everything appears to be OK.

---

