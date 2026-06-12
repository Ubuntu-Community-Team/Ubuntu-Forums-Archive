---
title: "Cookies and Internet Explorer 8"
date: 2009-10-10
forum: Programming Talk
---

### Post by Bacardil on 2009-10-10
I have learned that Internet Explorer 8 unlike previous versions can't open cookies from a home page/server, if they are opened via iframe or pictures (1x1 pixel).

Is there a way to work around this, or will it be changed, so it possible?

---

### Post by NoaHall on 2009-10-10
I haven't heard of that before, but creating a iframe works for me.

---

### Post by OpenGuard on 2009-10-11
Cookie stuffing is some sort of a crime.

---

### Post by froggyswamp on 2009-10-11
It can well be a bug. IE8 has been pushed earlier than its developers wanted for known reasons, I for one had issues with IE8 (final release) rendering Google's search page buttons extremely small.
IE8, work in progress.

---

### Post by Bacardil on 2009-10-11
I have tested with other affiliate systems, but since I have made my own for my own page, it would be nice that it also worked :).

Here follows a description of the system:

1.	The user clicks on an affiliate link
2.	The user is passe don to the affiliate system
3.	The affiliate system creates a cookie on the user&#8217;s computer
4.	The affiliate system transfers the user to the homepage of the advertisement
5.	The user create/byes or some ting else
6.	The user is transferred to a Receipt The PAGE
7.	On the Receipt The PAGE there is a 1x1 pixel picture referring to the affiliate system
8.	The picture is Loading by the user
9.	The affiliate system checkes if there is a lead cookie on the user&#8217;s computer
10.	If there is: The affiliate system adds a lead to the campaign
11.	The affilieate system returns the 1x1 pixel picture
This works just fine in firefox and IE7, but not IE8 and crome, why?

When the user uses IE8 the affiliate system can never find the cookie on the user&#8217;s computer as described in 9. although it was created in 3.

---

### Post by NoaHall on 2009-10-11
What language are you using to create the cookie?

---

### Post by Bacardil on 2009-10-11
The system is designed in PHP

---

### Post by NoaHall on 2009-10-11
Can I take a look at the code you're using to do it?

---

### Post by Bacardil on 2009-10-11
Yes, it's all code or any of the items you are interested in looking at?

---

### Post by NoaHall on 2009-10-11
The php code
- creating the cookie,
- redirecting the user
- and the 1 x 1 pixel image

---

### Post by Bacardil on 2009-10-11
I'll find some code within 10 minutes, using the Symfony Framework, so there will be missing some code, but hope you can help anyway

---

### Post by Bacardil on 2009-10-11
**Creation of COOKIE:**

$this->getResponse()->setCookie($campaign->getToken() . '-lead', strtotime($campaign->getRememberLeads()), strtotime($campaign->getRememberLeads()), '/');
$this->getResponse()->setCookie($campaign->getToken() . '-lead-publisher', $publisher->getUsername(), strtotime($campaign->getRememberLeads()), '/');

Redirecting the user

//Check if the banner object is set and the banner has an individual url address
if(is_object($banner) && $banner->getUrl())
{
  $this->redirect(Util::checkHttpPrefix($banner->getUrl()));
}
else
{
   // Use the campaign url.
   $this->redirect($campaign->getLink());
}

	
**The code around 1x1 pixel**

    $campaign = CampaignPeer::retrieveByPK($this->getRequestParameter('campaign'));
    $this->forward404Unless($campaign);
   
    // Check if the campaign is present in the users cookie.
    $publisherUsername = $this->getRequest()->getCookie($campaign->getToken() . '-lead-publisher');
    $publisher = sfGuardUserPeer::retrieveByUsername($publisherUsername);
    $this->forward404Unless(($publisher) && ($publisher->getProfile()->getUserType() == sfGuardUserProfile::TYPE_PUBLISHER));
    if(!$campaign->getIsDisabled())
    {
      // Register the lead
      $campaign->registerLead($publisher, $this->getRequest()->getHttpHeader('addr', 'remote'));
     
      //Reset the leads cookies
      $this->getResponse()->setCookie($campaign->getToken() . '-lead-publisher');
      $this->getResponse()->setCookie($campaign->getToken() . '-lead');
     
    }
    $this->setLayout(false);

---

### Post by NoaHall on 2009-10-11
Hm, and which bit doesn't work in IE8?

---

### Post by Bacardil on 2009-10-11
No, the system creates a cookie on the user's computer, but when it is in section 9 must find the cookie that is saved, so it can not find it, but it is only in Internet Explorer 8 - The previous version works perfectly.

---

### Post by NoaHall on 2009-10-11
Ah, I see.

Try inputing "print_r($_COOKIE);" to see if any cookies are stored at all.

I've never used that websystem before - I suggest you ask on their forums, you'll get more help.

---

### Post by Bacardil on 2009-10-11
Now I have checked and there are up cookies, but it still can not find a cookie when the system is called through the 1x1 pixel image. But I open the address directly to the 1x1 pixel image, so they can easily find the cookie

---

### Post by bobince on 2009-10-11
Have you put a [P3P](http://evolt.org/node/20756) policy up? Any service you make that relies on third-party cookies (by iframes etc.) must talk P3P for IE to allow it, and I believe WebKit (Chrome, Safari) has some support. This hasn't changed in IE8, though your defaults may vary.

Firefox has (had?) some code to support it, but hid it away in the config because basically P3P is a worthless waste of everyone's time.

---

### Post by hessiess on 2009-10-12
IE8 probably has 3rd party cookies disabled by default (which is a good thing)

---

### Post by Bacardil on 2009-10-12
Thanks for your reply. There has been looking a little on P3P, but did not think it worked, but we're testing just a little again and then returned

---

