---
title: "recaptcha and php"
date: 2009-05-19
forum: Programming Talk
---

### Post by ELD on 2009-05-19
Hi all i am programming a message board which has a quick reply and 
 seems to always say you got the captcha wrong.
 
 Test here: [http://www.prxa.info/area51/viewtopic.php?tid=78](http://www.prxa.info/area51/viewtopic.php?tid=78) 

 
Everywhere else works, registering, new topic, new reply (the full reply page) just not quick reply?


Would anyone be able to help me to find out why? I can send the code to anyone.

---

### Post by bvanaerde on 2009-05-19
I think it's best to copy the code here ;)
Just make sure you don't reveal any kind of passwords.

---

### Post by ELD on 2009-05-19
Okay well here is the quick reply function which resides in the pxb class:
```

    function quick_reply() 
    { 
        global $site_config, $parray, $templating, $lang; 
         
        // check if the quick reply is on and you can reply 
        if ($site_config['quick_reply'] == 1 && $parray['reply'] == 1) 
        { 
            if ($this->locked == 0) 
            { 
                // check if we need to do a captcha or not 
                if ($site_config['guest_captcha'] == 1 && $_SESSION['group'] == 4) 
                { 
                    if ($site_config['captcha_engine'] == 'pxb') 
                    { 
                        $guest_captcha = "{$lang['captcha_pxb']}<br />  
                        <img src=\"includes/captchas/captcha_pxb.php\" alt=\"captcha image\"><br /> 
                        <input type=\"text\" name=\"captcha\" size=\"3\" maxlength=\"6\"><br />"; 
                    } 
             
                    else if ($site_config['captcha_engine'] == 'maths') 
                    { 
                        $guest_captcha = "{$lang['captcha_maths']}<br /> 
                        <img src=\"includes/captchas/captcha_maths.php\" alt=\"captcha image\"><br /> 
                        <input type=\"text\" name=\"captcha\" size=\"3\" maxlength=\"6\"><br />"; 
                    } 
                     
                    else if ($site_config['captcha_engine'] == 'recaptcha') 
                    { 
                        require_once(PXB_ROOT . '/includes/captchas/captcha_recaptcha.php'); 
                        $publickey = "publickeyhere "; 
                        $guest_captcha = "{$lang['captcha_recaptcha']}<br />" . recaptcha_get_html($publickey); 
                    } 
                } 
                                             
                else 
                { 
                    $guest_captcha = ''; 
                } 
                                         
                // okay all god show the box 
                echo eval($templating->load('viewtopic', 'quickreply')); 
            } 
             
            else if ($this->locked == 1) 
            { 
                if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2) 
                { 
                    echo eval($templating->load('viewtopic', 'quickreply')); 
                } 
            } 
        }

```I include quick reply into other functions in that class by simply doing "$this->quick_reply();".

When the reply form is submitted it goes to newreply.php page:
Here is the captcha snippet:
```

    // if the captcha was entered wrong 
    if ($_SESSION['group'] == 4 && $site_config['guest_captcha'] == 1) 
    { 
        if ($site_config['captcha_engine'] == 'maths' || $site_config['captcha_engine'] == 'pxb') 
        { 
            if($_SESSION["captcha"] != $_POST["captcha"]) 
            { 
                $pxb->redirect("viewtopic.php?tid={$topic}"); 
                $pxb->error_message($lang['captchawrong']); 
            } 
        } 
         
        else if ($site_config['captcha_engine'] == 'recaptcha') 
        { 
            require_once(PXB_ROOT . '/includes/captchas/captcha_recaptcha.php'); 
            $privatekey = "private"; 
            $resp = recaptcha_check_answer ($privatekey, 
                            $_SERVER["REMOTE_ADDR"], 
                            $_POST["recaptcha_challenge_field"], 
                            $_POST["recaptcha_response_field"]); 
             
            if (!$resp->is_valid)  
            { 
                $pxb->redirect("viewtopic.php?tid={$topic}"); 
                $pxb->error_message("{$lang['captchawrong']} <a href=\"viewtopic.php?tid={$topic}\">{$lang['return']}.</a>"); 
            } 
        } 
    }

```(note that works perfectly when submitting from the main reply page, but not quick reply? Which is the problem i am trying to fix!)

---

### Post by bvanaerde on 2009-05-19
It is going wrong here:
> if($_SESSION["captcha"] != $_POST["captcha"])
So, what you can do, is echo both variables.
I'm guessing one of those variables is always empty for some reason.

edit: are you suppressing warnings/error on your website? If you say that the captcha works on another page, maybe there's a problem with defining the correct path to the include files.

---

### Post by ELD on 2009-05-19
> **bvanaerde said:**
> It is going wrong here:

So, what you can do, is echo both variables.
I'm guessing one of those variables is always empty for some reason.

That is not for the recaptcha the is for my other built in ones, the recaptcha part is below that.

Recaptcha bit starts here:
```

else if ($site_config['captcha_engine'] == 'recaptcha')
[FONT=monospace]
```
[/FONT]

---

### Post by bvanaerde on 2009-05-19
Ok, sorry :o
But I'll give the same advice:
>             $resp = recaptcha_check_answer ($privatekey, 
                            $_SERVER["REMOTE_ADDR"], 
                            $_POST["recaptcha_challenge_field"], 
                            $_POST["recaptcha_response_field"]); 

echo **$_POST["recaptcha_challenge_field"]** and [B]$_POST["recaptcha_response_field"]
[/B]
Also: shouldn't it be "elseif" instead of "else if"?

---

### Post by ELD on 2009-05-19
The challenge field is encrypted and the response shows i entered it in fine.

And no it shouldn't it is personal preference for me to put a space in between the words, just looks tidier.

---

### Post by bvanaerde on 2009-05-19
> Notice: Undefined variable: edited in /home/prxainfo/public_html/area51/includes/class_topics.php(275) : eval()'d code on line 24
I'm guessing you're working on the page right now :D

I don't know if the "else if" thingie is causing problems, but for me it looks like you've got two else clauses right after eachother, which can't be right.

---

### Post by ELD on 2009-05-19
Like i said it works else where but just not from this one point. Seriously "else if" will not cause a problem trust me it is a simple space between two words i use it all the time, and having and else after an else will not cause a problem either. Do you use php by the way, from those questions to me it seems you don't? I don't mean to sound rude but i really do need to fix this, it is driving me nuts.

Those undefined things are from me turning error reporting on, nothing to do with the recaptcha system.

---

### Post by ELD on 2009-05-20
I will now pay $10 via paypal to whoever can fix it, code is here:[http://www.prxa.info/archives/Upload.tar.gz](http://www.prxa.info/archives/Upload.tar.gz)

---

### Post by bvanaerde on 2009-05-20
> **ELD said:**
> I will now pay $10 via paypal to whoever can fix it, code is here:
[http://www.prxa.info/archives/upload.tar.gz](http://www.prxa.info/archives/upload.tar.gz)
I believe this is the correct link:
[http://www.prxa.info/archives/Upload.tar.gz](http://www.prxa.info/archives/Upload.tar.gz)
As you can see, errors can be something ridiculously simple but still hard to find ):P

---

### Post by ELD on 2009-05-20
My bad fixed the link, still stands $10 via paypal to who can fix.

---

