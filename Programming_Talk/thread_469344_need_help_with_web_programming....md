---
title: "need help with web programming..."
date: 2007-06-09
forum: Programming Talk
---

### Post by hockey97 on 2007-06-09
Hi I made 2 animations for 2 button state's, now I need to code them and really need help with this I googled stuff but never found my answer.

I got 2 art's for a button in one for normal state or up state, and one for over state,  I then want to play an animated  button so when you click on the button the button play's it's aniamtion at and if the person clicks again it play's another animation.

what I am trying to do is make a e-mail form, I want to play animation  one when pressed it get's played, i want to check if the e-mail is still being proccessed or being sent if it is then  if the user clicks the button again another animation play's which say's please wait.

Does anyone know how to do this?? I tried in html and also java how ever I get a still frame, like my animaitons don't run it's just one frame it only displace the first frame of my animation and taht's it.

I was thinking to do this in python??

Could someone help me out here??? point me to any website with tut's that explains or could answer what I want.

---

### Post by pmasiar on 2007-06-09
wiki in my sig has links to many resources. WebApplication page shows how to make very simple dynamic page in Python. 

Are you interested in artistic part of web apps, or in basic functionality? Those are rather different worlds, and usually they do not mix much. Different skills, different tools, different interests... :-)

---

### Post by hockey97 on 2007-06-10
I am a little both, I just right now working on my website I am going  to give e-mail service ect, so I am working on the e-mail part page and I right now am working on the form page where the user iput's e-mail adress and also subject and gives a message to send, I know how to do these in html ect.

But I can't find a way to play my long animated submit button but I want conditions involve, like first off when you click the submit button I want my frist animation saying the e-mail is being sent, and if the procces is still going and the user click the submit button again,  then another animation pay's saying wait...

So what want some condition with it.

I know in html it can't handle such a thing, I tried java but it dosen't play my animation it play's my first frame of the animation and not all the other frames.

Is their a way that when the person clicks the button my animation is played like it's long it's 68 frames.

---

### Post by barmazal on 2007-06-10
is your animation is a .gif file? I don't think anything on earth can make .gif file stop.

what you can do are two things, either turn to windows and make a Flash animation which will be controlled (handle on rollover, press and so on) via Action Script

or

if you want Ubuntu
use Ajax which won't give you full control over animation but will be able to create some neat stuff, seamless to Flash but not exact as you want it

Ajax frameworks you can use are Dojo or Mootools, both have FX engine.

---

### Post by hockey97 on 2007-06-10
Well I am making animaations for buttons, does flash do this?? this is not any button it's a submit button,

I want it that when the user clicks the submit button an animation play's, and ya it's in a GIF formate,
I even did trying putting it in a .swf formate, I have flash studio 8 , Is action script easy???

I am working on the interface of my e-mail service and right now working on the e-mail form where you send a message to someone else.

when the person clicks the submit my animation supposed to run, I made an animation showing the submit

button is in flames and the flames slowly ingolf's the button and then fades and an envolope fades in saying

message is sending, but I want to be able that when this animation is still being played or if the message is

still getting sent then when the user clicks on the animation then it will play a waiting animation saying

please wait....  So that's where I am at right now, I do know python but never made a full program yet,

I did make small programs like a calculator wihit a gui using thinker. 

Is apache able to play ur boradcast flash media??

becuse later on I plan to make an  intro to my website using flash but also I would love to add sound's and music to the flash media.

Thanks for your time.

---

### Post by pmasiar on 2007-06-10
> **barmazal said:**
>  I don't think anything on earth can make .gif file stop..

I am not JS/AJAX expert, but IIUC you *could* modify DOM to replace  animated .gif with a static one, no?

Also, there are many more JS libraries, like jQuery, scriptaculous, prototype, etc. Recently, Yahoo UI had a menu exactly as I wanted. Do you know some good resources comparing pro and cons of all those JS libraries?

---

### Post by nitro_n2o on 2007-06-10
> **hockey97 said:**
> Well I am making animaations for buttons, does flash do this?? this is not any button it's a submit button,.
Yes Flash can do this

> **hockey97 said:**
> I want it that when the user clicks the submit button an animation play's, and ya it's in a GIF formate, I even did trying putting it in a .swf formate, I have flash studio 8 , Is action script easy???
You can integrate your button easily in the website if you are using Dreamweaver... and don't use gif in flash: the .swf will be really heavy. Use action script for your animation it's not difficult, and there are so many tutorials and code. And playing swf is not related to apache as far as i know.. it depends on the clients if they have the flash player

You can do so many things in flash :) even more than what really need right now.. But you need to have a back up plan for people who don't have a flash player. you can either redirect them to adobe website to download flash, or you can silently load static images instead. 

good luck

---

### Post by hockey97 on 2007-06-10
So do you think I can add my 68 frame animation of the submit button that is activated when the submit button is pressed.

I am going to explore more of flash.

I use dreamweaver  and tried making the buttons but still when I put that animaiton it gives me an error saing not enough frames, so it add's more, then I go to preview well I press F12 and tested the button it 

only show's the the image of the button_up when I put my mouse over it it dosen't do anything , I have a image made for when the pointer is over the button it's a hilighte's the button it's supposed to.

but dosen't, even when I click the button it dosne't play my animation this is in dreamweaver.

I never seen coding for making a custom submit button.

---

### Post by CptPicard on 2007-06-11
If you're working with the usual request-response cycle that refreshes the complete page, I am not sure you even have control over this sort of functionality... if I tried doing this without AJAX, I'd probably use an animated gif that catches clicks and operates so that on first click it submits the form and switches the gif to the send animation and sets a boolean flag variable, and if a subsequent click is received while the response still has not rendered (we know this by checking the variable), it furthermore switches the gif to the "please wait" animation. IF the browser doesn't stop running scripts by the first click, this should all be doable by fairly simple Javascript.

I don't know how big these emails are you're sending with your form, but it should be noted that it is unlikely that sending would actually take so long that people would really get a chance to see this "wait"-animation of yours. It's different of course if you've got a huge attachment to upload or something like that.

AJAX may be an option, but I have a fleeting suspicion that unless there is a ready-made component for this, you'd be totally out of your depth with it...

---

### Post by LollYouSuckZor on 2007-06-11
Can you not take a screenshot of the rollover image you want it to be, then replace one of the Gif's with that?... And code it to where it was a rollover?.  Im a web designer, so if theres a problem or any questions, mabey im not hitting the right spot? Message me?

---

### Post by hockey97 on 2007-07-06
well I stop working on tmy site, I am trying to start an ISP business, I wanted to provide e-mail service, 
what I wanted to do was,

that when your writting an e-mail to someone,  I when you submit it clicking the  customesubmit button I made, the button would then play it's sending animation which is the button burns while the flames go down the button it turns into an Letter/ envolope which then when the flames burned every part meaning it completely turn the button to an envolope, it would then show the envolope ripping though the backround,
and showing streaming numbers 10101 binary basicly, that's the sending animation,

after that or while it's playing that  if the user clicks it an animation would play saying please wait after that animation is played then if the e-mail is still being proccesed to be sent or still trying to send it then it would go back to the sending animation, after it's done I would take the user to a page that say's it's been sent,
thanks for your time and then their are side notes saying if having trouble how to contact us.

I am trying to make my website look high-tech meaning like a porfessional website making it look like a game site with all the 3d models ect and making it interactive, ect.

but I made my animations in .gif format, I made the html code, and the php code to send the e-mail.

but when I tried it I only got the first frame of the animation the animation wouldn't play, I had the custom button and then when click it would show the beginning of the flames , which is in the first frame of my animation.

I kinda stoped on working on it, due to I have some troubles on getting the business started.

---

