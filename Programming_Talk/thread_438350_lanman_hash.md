---
title: "lanman hash"
date: 2007-05-09
forum: Programming Talk
---

### Post by cdenley on 2007-05-09
I'm trying to write a php function that can generate an LM hash for samba. The hash it creates does not match existing hashes in the configuration. I know I have the right password, because the NT hash does match. I'm pretty sure I'm using the right encryption method, because on passwords shorter than 8 characters, the second half of the LM hash matches. I'm not sure how to test it, since I don't have any Windows 9x clients, but from what I read, the hash is always going to be the same for a given password.

```
function lmhash($lmpass)
{
	$lmpass=strtoupper($lmpass);
	if(strlen($lmpass)>14)
		$lmpass=substr($lmpass,0,14);
	while(strlen($lmpass)<14)
	{
		$lmpass.=chr(0);
	}
	$lmstr="KGS!@#$%";
	$half=substr($lmpass,0,7);
	$ret =strtoupper(bin2hex(mcrypt_ecb(MCRYPT_DES,$half,$lmstr,MCRYPT_ENCRYPT,mcrypt_create_iv(8))));
	$half=substr($lmpass,7);
	$ret.=strtoupper(bin2hex(mcrypt_ecb(MCRYPT_DES,$half,$lmstr,MCRYPT_ENCRYPT,mcrypt_create_iv(8))));
	return $ret;
}
```

---

### Post by gcopenhaver on 2008-05-09
This is a pretty old thread (1 year to be exact, lol), but I was recently searching for information for performing the LM hash in javascript and came across this post.  I couldn't find anything related to the LM hash and javascript, and this was the most complete function I've found (without looking at source code of things like ophcrack or anything like that).  After looking at [http://en.wikipedia.org/wiki/LM_hash](http://en.wikipedia.org/wiki/LM_hash) I found that this function has a couple problems with it.

First, although the password is split into two 7-character uppercase portions, there's another step that's required to turn them into DES keys for encrypting.  You need to add a '0' bit after every 7 bits in each 7-byte string to turn each half into 8-byte (64-bit) DES keys.  This took me many hours to figure out how to do in javascript with as little code as possible, but I finally figured it out.

I have not ported my javascript code to PHP yet, but will soon, and I will post it back here when I do.  You can view the javascript code here: [http://gcopenhaver.com/node/94](http://gcopenhaver.com/node/94)

---

### Post by gcopenhaver on 2008-05-13
I found a php script called randpass at [http://www.finnie.org/software/randpass/](http://www.finnie.org/software/randpass/) which does LM Hashes.  I liked the way it does it better than my JavaScript code, too, so I based my JavaScript code on it, and it works fine.  The only is that my JavaScript code doesn't produce the correct hash when supplying the DES function with the same IV's as the PHP code does...kinda strange, but I haven't looked into that much.  I'm not sure why they did a couple other things in the code, but I just ignored or changed them when porting to JavaScript.

---

