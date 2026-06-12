---
title: "Medical"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by Paper Pusher on 2012-04-05
I want to correspond with my doctor over e-mail.
She has legitimate concerns about the privacy of the communication.
(phone and fax are OK).

Is there something simple I can do to satisfy her concern?
The communication comprises text and JPEGs.  I'm thinking of encrypting the message with True Crypt and attaching it to my e-mail.

---

### Post by terrykiwi83 on 2012-04-05
get a free Comodo Digital Email certificate and encrypt your email. I use a free certificate with my Evolution. You could also use OpenPGP?

---

### Post by winh8r on 2012-04-05
> **Paper Pusher said:**
> I want to correspond with my doctor over e-mail.
She has legitimate concerns about the privacy of the communication.
(phone and fax are OK).

Is there something simple I can do to satisfy her concern?
The communication comprises text and JPEGs.  I'm thinking of encrypting the message with True Crypt and attaching it to my e-mail.
  
PGP / GPG encryption would work but the doctor is probably more concerned about this sort of thing:

[http://www.medicalprotection.org/uk/england-factsheets/communicating-with-patients-by-fax-and-email]("http://www.medicalprotection.org/uk/england-factsheets/communicating-with-patients-by-fax-and-email")

A lot of medical practitioners will not use email due to the inherent security risks concerning unauthorised disclosure of personal data.Security at the practice end might also be an issue if the emails are accessible by staff who may not be fully authorised to access that information.

I am sure you understand that your doctor does not just have to consider your case in this way, there would need to be a full policy statement drawn up and agreed with the regulatory body (GMC in the UK)

---

### Post by Paper Pusher on 2012-04-05
Thanks for the quick response.  I'm open to anything.  Do you have a particular client program in mind?

---

### Post by Paper Pusher on 2012-04-05
winh8r.  I understand. I already have her e-mail address and we've used it.
I merely want to be prepared in case the issue arises.

---

### Post by winh8r on 2012-04-05
You could use something like [enigmail]("http://enigmail.mozdev.org/home/index.php.html") with Thunderbird mail client which is in the repositories / software centre.

Hope this helps.

---

### Post by 0011235813 on 2012-04-05
> **winh8r said:**
> You could use something like [enigmail]("http://enigmail.mozdev.org/home/index.php.html") with Thunderbird mail client which is in the repositories / software centre.

Hope this helps.

I concur. Open up Thunderbird, configure your email (if you haven't done so already) and then go to tools, add-ons. Search for "Enigmail" (without the quotations) and click install. Then restart Thunderbird. 

Now go to OpenPGP- key management. Click "generate", and go through the wizard.

NOTE: Your GP will be unable to read the message if she doesn't have the key!! You must first give her the .asc key. I would suggest you give a her the USB stick containing the key. Also, I think she needs Thunderbird, so be sure to mention that.

PS: What do they mean by "encryption"? Gmail uses https AES-256bit encryption, does that count?

---

### Post by Paper Pusher on 2012-04-05
Thanks for the suggestions.  But I don't know what mailer her office uses.

---

### Post by 0011235813 on 2012-04-05
> **Paper Pusher said:**
> Thanks for the suggestions.  But I don't know what mailer her office uses.
 In any case, she will still require the application you used to encrypt the email or attachment. If she doesn't have Thunderbird, she can't use Enigmail. If she doesn't have TrueCrypt, she can't decrypt the container. You'll have to ask.

---

### Post by Paper Pusher on 2012-04-05
You're quite right.  She has to have something.
I'm assuming that installing TB is harder than TC for extreme low use.

---

### Post by Paper Pusher on 2012-04-05
> **0011235813 said:**
> Gmail uses https AES-256bit encryption, does that count?

Do both parties have to use gmail? or is this widely used.

---

### Post by Lars Noodén on 2012-04-05
> **Paper Pusher said:**
> Do both parties have to use gmail? or is this widely used.

No.  It's enough that both parties use PGP.

---

### Post by 0011235813 on 2012-04-05
> **Paper Pusher said:**
> You're quite right.  She has to have something.
I'm assuming that installing TB is harder than TC for extreme low use.
Not really, TrueCrypt is a pain to use. I've tried using it, and even though I'm by no means what you'd call a novice, I still found it difficult.

---

### Post by Paper Pusher on 2012-04-05
> **0011235813 said:**
> Not really, TrueCrypt is a pain to use. I've tried using it, and even though I'm by no means what you'd call a novice, I still found it difficult.

Thank you for letting me know.
Do you know of a better solution?

---

### Post by 0011235813 on 2012-04-05
> **Paper Pusher said:**
> Thank you for letting me know.
Do you know of a better solution?

Well cryptkeeper works very nicely and is easy to use, plus it integrates well into Linux. However, it might not be ideal if you plan on transferring top secret files, and worst of all- I'm not sure if it will work in other operating systems. 

I imagine there are various other solutions out there, you should check the repositories.

---

### Post by SeijiSensei on 2012-04-05
If your doctor practices in the United States, sending unencrypted email to patients constitutes a violation of the law called HIPAA.  If she works with a hospital, HMO, or other large medical practice, chances are good that they have already installed a web-based system to communicate with patients.  If she's a sole practioner or in a small group with limited IT resources, use the telephone.

I think it's unreasonable to expect your doctor to jump through the hoops required to set up encrypted email just to communicate with you.

---

### Post by Paper Pusher on 2012-04-05
> **SeijiSensei said:**
> If she's a sole practioner or in a small group with limited IT resources, use the telephone.

Is the telephone a secure  communications channel?

---

### Post by HeroOfCanton on 2012-04-05
> **Paper Pusher said:**
> Is the telephone a secure  communications channel?

Much more secure than email in general. By a good margin.

I have clients that are in medical fields and HIPPA laws are very finicky. They (and therefore I) have to be very very careful as to how medical data is transferred. You're probably going to have to pick up the phone.

In addition to the other suggestions, you could also create a self extracting .exe and provide the doctor with a password, but then you'd have expect them to do the same for reverse communications. Probably not going to happen.

---

### Post by andrew.46 on 2012-04-05
> **winh8r said:**
> PGP / GPG encryption would work but the doctor is probably more concerned about this sort of thing:

[http://www.medicalprotection.org/uk/england-factsheets/communicating-with-patients-by-fax-and-email]("http://www.medicalprotection.org/uk/england-factsheets/communicating-with-patients-by-fax-and-email")

Note the comment about the use of fax:

> 
MPS has dealt with a number of cases where information has been picked up by the wrong person, often because of misdialling or out-of-date fax numbers. This can mean that patient confidentiality is breached and treatment is delayed, due to the time lapsed until the information reaches the correct person. 


Not just the risk of misdialling but you have to consider the physical layout of an office: where is the fax machine, who picks up the faxes, is it a combined fax/printer/copier used by multiple people etc. It seems a little too easy to jump on security issues relating to email before looking at simple mechanical issues of other technologies such as fax.

---

### Post by Dangertux on 2012-04-05
In terms of HiTech compliance (which is what your doctor is concerned about)

There are two types of encryption. At rest and in transit.

In transit encryption is the line level encryption used (TLS).

At rest is the data encryption used (PGP) note, GPG is not FIPS 140-2 compliant (accordance with HiTech) GPG2 however IS , due to the fact that GPG supports weaker cryptographic ciphers.

In order for PHI to meet HiTech compliance , data must be encrypted in transit AND in rest.

Now -- that being said, the data you're providing might not be considered PHI. PHI must contain certain things.

For instance, an example of PHI would be.

Patient Name
Patient Address
Patient Treatment plan


Where as Patient Date of Birth and Treatment plan , probably would not be considered PHI (less identifying information)

Hope this helps.

---

### Post by Dreamer Fithp Apprentice on 2012-04-05
Neither Truecrypt nor any other symmetric encryption is really appropriate to the task. This is exactly what PGP/GPG public key encryption is for. Each party generates a public key and communicates it to the other by any channel that is convenient - it doesn't have to be secure. It can be published openly, put on your web site or business card. Then ANYBODY can send you a secure message that only you can decrypt because the DECRYPTION procedure cannot be derived from knowledge of the ENCRYPTION procedure. It sounds counterintuitive if you aren't familiar with it but the math is sound.

Realistically though, the average M.D. isn't very smart about this sort of thing. I know people like to believe they are superhuman intellectual demigods, but close contact with enough of them will cure you of that delusion. And generally speaking they are legitimately pressed for time. So unless some support staff, such as would be more likely in an institutional setting, has already set this up, or they know you well enough to be comfortable letting you set it up for them, or they are the rare example of an M.D. who is also a bit of a technophillic nerd, or perhaps if some good software salesperson sold them a medical practice package that included this, set it up for them so that it was easy to use (which of course it should be), and showed them how to use it -- they aren't likely to consider taking the time to learn this stuff well enough that they can be confident that it is as it is represented to be, that they understand it correctly, and that they aren't stepping on some sort of legal landmine. And I can't really blame them. In a truly free society with freedom of contract and a free market they would probably be more flexible. But in most countries they have no choice but to practice in a defensive paranoid mode.

---

### Post by SeijiSensei on 2012-04-05
> **Dangertux said:**
> Now -- that being said, the data you're providing might not be considered PHI. PHI must contain certain things.

Things that might at first glance not be considered as PHI definitely are.  I recently built an online appointments system for a medical client.  At no time is the appointment information sent to the patient.  Rather the patient receives an email notice when the appointment is made and must log into a secure website to obtain the details.

Why?  Well, suppose the physician is an oncologist, and the patient is at work.  Now imagine a nosy boss reads the patient's email, sees the doctor's name, looks her up and discovers her specialty.  Now the boss knows that the patient may have cancer.  This is precisely the kind of situation HIPAA is designed to protect against.

---

### Post by bodhi.zazen on 2012-04-05
> **SeijiSensei said:**
> If your doctor practices in the United States, sending unencrypted email to patients constitutes a violation of the law called HIPAA.  If she works with a hospital, HMO, or other large medical practice, chances are good that they have already installed a web-based system to communicate with patients.  If she's a sole practioner or in a small group with limited IT resources, use the telephone.

I think it's unreasonable to expect your doctor to jump through the hoops required to set up encrypted email just to communicate with you.

This ^^

If your doctor does not already have such a system, they will soon.

---

### Post by 0011235813 on 2012-04-06
> **HeroOfCanton said:**
> Much more secure than email in general. By a good margin.

I have clients that are in medical fields and HIPPA laws are very finicky. They (and therefore I) have to be very very careful as to how medical data is transferred. You're probably going to have to pick up the phone.

In addition to the other suggestions, you could also create a self extracting .exe and provide the doctor with a password, but then you'd have expect them to do the same for reverse communications. Probably not going to happen.

I wouldn't be so sure, telephone calls can easily be tracked, whereas it's much easier to hide emails by routing them through a proxy, like tor. Second, connections can easily be interpreted, which is much harder for emails that use TSL encryption and AES-256bit algorhythm. I think it is what DT said about somebody going into her computer and obtaining the details. In which case, it is her own responsibility to encrypt her own emails.

---

### Post by I2k4 on 2012-04-06
In Windows, my go to for sending encrypted files or folders by email is 7Zip.

My guess is a) the doctor can't deal with Linux-specific alternatives if she uses Windows, and b) she would require an installation and some experience with TrueCrypt to access a TrueCrypt container with relevant files.  

I'm new to Linux, but it appears that 7Zip, which I've used on Windows, is available on Linux and it likely has the same encryption functionality in Linux that it does in Windows:  

[http://www.7-zip.org/download.html](http://www.7-zip.org/download.html)

You should obviously test the functionality with the recipient before relying on it.

---

### Post by 0011235813 on 2012-04-06
> **I2k4 said:**
> In Windows, my go to for sending encrypted files or folders by email is 7Zip.

My guess is a) the doctor can't deal with Linux-specific alternatives if she uses Windows, and b) she would require an installation and some experience with TrueCrypt to access a TrueCrypt container with relevant files.  

I'm new to Linux, but it appears that 7Zip, which I've used on Windows, is available on Linux and it likely has the same encryption functionality in Linux that it does in Windows:  

[http://www.7-zip.org/download.html](http://www.7-zip.org/download.html)

You should obviously test the functionality with the recipient before relying on it.
 Are you sure the method you are suggesting uses an encryption algorhythm strong enough to be considered effective in this scenario?

---

### Post by I2k4 on 2012-04-06
The Windows version I'm familiar with provides AES-256 (the same as the TrueCrypt default algorithm) - as you'll see from the link, the Linux derivative is "unofficial" but seems to offer the same app.  If I was sending medical info I'd dig deeper into this, as well as be sure the doctor can unpack it reliably. If it's all good, it solves the problem.

---

### Post by Dangertux on 2012-04-06
> **SeijiSensei said:**
> Things that might at first glance not be considered as PHI definitely are.  I recently built an online appointments system for a medical client.  At no time is the appointment information sent to the patient.  Rather the patient receives an email notice when the appointment is made and must log into a secure website to obtain the details.

Why?  Well, suppose the physician is an oncologist, and the patient is at work.  Now imagine a nosy boss reads the patient's email, sees the doctor's name, looks her up and discovers her specialty.  Now the boss knows that the patient may have cancer.  This is precisely the kind of situation HIPAA is designed to protect against.


You missed my point, if you look at the example I said of what is not it said DATE OF BIRTH and TREATMENT plan. This does not meet the criteria of PHI because it is not personally identifiable as per.

[http://www.hipaa.com/2009/09/hipaa-protected-health-information-what-does-phi-include/](http://www.hipaa.com/2009/09/hipaa-protected-health-information-what-does-phi-include/)

---

