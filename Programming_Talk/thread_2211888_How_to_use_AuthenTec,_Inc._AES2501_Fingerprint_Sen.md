---
title: "How to use AuthenTec, Inc. AES2501 Fingerprint Sensor in bash script"
date: 2014-03-18
forum: Programming Talk
---

### Post by mariusz-ciszewski on 2014-03-18
Could you please help me how to use USB fingerprint reader in bash script to make possible accept or reject user?

For example 

Ubuntu is asking (console):

"Please scan your finger."

And then (based on result) we can have:

"You was recognized as Mariusz. Hello Mariusz" (and accepted.sh will be executed then)

or

"I cannot to find you in my database. Sorry" (and rejected.sh will be executed then)

[FONT=arial]My fingerprint is:

Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor

Could you please try to help me? I was asking / tried a lot of times in many places but I cannot to find any support in this topic. 

I need it to run my home security system ( [/FONT]http://rasp485berry.wordpress.com/ )
[FONT=arial]
[/FONT][FONT=arial]Thank you very much for any help.[/FONT][FONT=arial]

Best regards
Mariusz Ciszewski.[/FONT]

---

### Post by mariusz-ciszewski on 2014-03-18
Sollution:

1. First fingerprint scan:

```
root@msi:/home/mariusz# fprintd-enroll
Using device /net/reactivated/Fprint/Device/0
Enrolling right index finger.
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-completed
```


2. Verification:

```
root@msi:/home/mariusz# fprintd-verify
Using device /net/reactivated/Fprint/Device/0
Listing enrolled fingers:
 - #0: right-index-finger
Verify result: verify-match (done)
```


3. Time interval effect exist

You can check it playing with this script:

```
#!/bin/sh


res=`timeout 5 fprintd-verify | grep result`


if [ "$res" = "" ]
 then
 echo "`date +%Y.%m.%d-%T` - rescan to fast, please wait a few seconds..."
 fi


if [ "$res" = "Verify result: verify-match (done)" ]
 then
 echo "`date +%Y.%m.%d-%T` - acces confirmed"
 fi


if [ "$res" = "Verify result: verify-not-match (done)" ]
 then
 echo "`date +%Y.%m.%d-%T` - acces dennied"
 fi
```

---

### Post by mariusz-ciszewski on 2014-03-18
But this sollution is valid for one user only (and one finger only). 

If I need to use it for more than only one user it is not possible.

So I'm still searching for sollution for many users. 

Please let me know if there are any other ideas.

---

