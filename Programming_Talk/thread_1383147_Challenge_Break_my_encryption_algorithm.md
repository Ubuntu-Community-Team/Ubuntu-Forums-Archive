---
title: "Challenge: Break my encryption algorithm"
date: 2010-01-16
forum: Programming Talk
---

### Post by JamesWhisker on 2010-01-16
This is an encryption function I wrote for simple, painless and non-libary dependent encryption. I challenge you to break it (for fun). I hope it doesn't have any major flaws.

[PHP]

define("SIMPLE_CRYPT_SALT", "\xf8\x87\x00\x63\x5a\x36\xf5\x19\xb6\x2a\x94\x4b\x09\x83\x41\x31");

    /**
    * @desc Encrypts the cleartext, returns an encrypted base64 encoded string with a linear sized compared to input size.
    */
    public static function simple_crypt($cleartext, $password) {
        // Append verification.
        $cleartext .= md5(SIMPLE_CRYPT_SALT . $cleartext, true);
        // Append padding.
        $pad_length = 16 - (strlen($cleartext) % 16);
        if ($pad_length == 0)
            $pad_length = 16;
        $cleartext .= "\x01" . str_pad('', $pad_length - 1, "\x00");
        // The first block contains the salt.
        $crypttext = $block = md5(mt_rand() . mt_rand() . SIMPLE_CRYPT_SALT . mt_rand(), true);
        $pwdblock = $password;
        for ($i = 0; $i < strlen($cleartext); $i += 16) {
            // Transform password block using cleartext.
            $pwdblock = md5($block . SIMPLE_CRYPT_SALT . $pwdblock . $password, true);
            // Get cleartext block.
            $block = substr($cleartext, $i, 16);
            // Encrypt it.
            $crypttext .= $block ^ $pwdblock;
        }
        // Encode and return.
        return base64_encode($crypttext);
    }

    /**
    * @desc Decrypts the cryptotext outputted from simple_crypt with the given password.
    * @desc Returns FALSE if decryption failed.
    */
    public static function simple_decrypt($crypttext, $password) {
        // Decode.
        $crypttext = base64_decode($crypttext);
        // Need to contain at least 3 blocks.
        if (strlen($crypttext) < 3 * 16)
            return false;
        // Partial blocks not allowed.
        if ((strlen($crypttext) % 16) != 0)
            return false;
        // The first block contains the salt.
        $block = substr($crypttext, 0, 16);
        $pwdblock = $password;
        $cleartext = '';
        for ($i = 16; $i < strlen($crypttext); $i += 16) {
            // Transform password block using cleartext.
            $pwdblock = md5($block . SIMPLE_CRYPT_SALT . $pwdblock . $password, true);
            // Decrypt cryptext block.
            $cleartext .= $block = substr($crypttext, $i, 16) ^ $pwdblock;
        }
        // Remove padding.
        $pad_pos = strrpos($cleartext, "\x01");
        if ($pad_pos === false || $pad_pos < strlen($cleartext) - 16)
            return false;
        $cleartext = substr($cleartext, 0, $pad_pos);
        // Slice verification from cleartext.
        $verification = substr($cleartext, -16);
        $cleartext = substr($cleartext, 0, -16);
        // Verify and return result.
        return ($verification == md5(SIMPLE_CRYPT_SALT . $cleartext, true))? $cleartext: false;
    }
[/PHP]Yes, I know md5 has been attacked, but I'm fairly certain those attacks cannot be used in this case. This thread is not a discussion about md5. Just pretend that md5() is a perfect hashing algorithm.

Here is a schematic view for your convinience:

[[IMG]http://img269.imageshack.us/img269/7426/simplecryptscheme.th.png[/IMG]]("http://img269.imageshack.us/i/simplecryptscheme.png/")[URL="http://img269.imageshack.us/img269/7426/simplecryptscheme.png"]
[/URL]

---

### Post by JamesWhisker on 2010-01-19
Forgot to mention that the definition of "break" here is beeing able to recover even a single byte of cleartext in any scenario where you can choose to know any other cleartext beforehand.

Also feel free to give comments, suggestions and ideas on the algoritm. How would you have chosen to encrypt text in PHP without non default extentions/modules?

~Shameless Selfbump~

---

### Post by Hellkeepa on 2010-01-19
HELLo!

Haven't given your scheme a test, as I don't have any time to play around with it I'm afraid.
Though, in those instances I have to encrypt something, and I couldn't rely on the standard libraries. I'm re-implement one of the accepted algorythms for this, instead of trying to outwit the entire cryptology field. I know I'm not *that* smart. :-P

Happy codin'!

---

### Post by JamesWhisker on 2010-01-19
I just felt that if you took an existing hashing function, turning it into an encryption function should be cake. This is fairly simple and I can't really think of any ways you could break it. 

My chain of reasoning goes something like this:


[LIST]
[*]Crypttext is XOR'ed by the output of MD5 and the Cleartext. So to know the cleartext, you have to know the output of the MD5.
[*]To know the output of the MD5 you have to know the input of the MD5, and you can't use the output to determine the input. (this is the layman definition of a perfect hash function)
[*]So as long as the MD5 input has over ~2^64 possible combinations (depends on the key length) the function should be safe from beeing broken by brute force.
[/LIST]
The ~trying to outwit the entire cryptology field~ that you speak about doesn't apply. That magic still takes place in the hashing function.

Another "side" attack is to take two cryptotexts that where encrypted with the same key, and where you know the cleartext in one of them. You can then extract the keystream and decrypt the other cryptotext without the key. This is prevented by standard Initialization Vector technique. The IV is 128 bit long with a total of 2^128 combinations. For this attack you would need two cryptotexts with the same IV, which is simply not going to happen in the age of this universe.

---

### Post by hessiess on 2010-01-19
DO NOT try to develop your own encryption algorithm, it WILL be insecure! If you actually need encryption, use a well `hammered on' algorithm like AES or Blowfish.

No, you cannot tern a hash function into an encryption function, the whole point of an encryption algorithm is that you can decrypt it again, the whole point of hashes is that they are one way functions! MD5 is broken because it has bean proven possible to generate two paces of clear text with the same hash.

---

### Post by Reiger on 2010-01-19
No MD5 is not broken in that sense. Every hashing function is surjective but not injective (the combination of that means hashing functions are not by definition bijective and therefore do not by definition have an inverse function). Which is why &#8216;collisions&#8217; and &#8216;buckets&#8217; are such a big deal with hash-based data structures.

---

### Post by MadCow108 on 2010-01-19
because of that hashes are considered broken when someone manages what hessies said. Even SHA-1 is cryptographically broken, although its less serious
Being able to generate 2 different versions of a similar but different content and the same hash makes the hash useless as a signature.

and its done for md5 in with only a reasonable amount of work (compared with the broken SHA-1 where the amount is still beyond practical use)

and to emphasize again:
never develop your own encryption algorithm! (except you really have years of time and a lot of knowledge)
its done all the time, especially in the commercial area, and in 99% of times the people fail. (just look at "encrypted" usb sticks... even the certified ones suck)

---

### Post by JamesWhisker on 2010-01-19
> **hessiess said:**
> No, you cannot tern a hash function into an encryption function, the whole point of an encryption algorithm is that you can decrypt it again, the whole point of hashes is that they are one way functions! MD5 is broken because it has bean proven possible to generate two paces of clear text with the same hash.

Obviously, I just did, so please elaborate what you mean... Also, If you want to state the obvious you could also add that apples and oranges are fruits and that there's nights between days.

And here we go... just replace MD5() with another hash function then. Pretend that MD5 is an unbroken perfect hashing algoithm. As I stated in the first post this thread is not about the security of MD5().

And yes, it would be obviously better to use an existing encryption function for security. But that's beside the point. This thread was ment to be a technical discussion, I'm not looking for generic programming guidelines. If you want to add a more specfic attack that could be launched against this encryption function, then go ahead.

An analogy would be something like: I'm trying to discuss how radio technology works and explain a circuit I built from diffrent parts. This is exactly like bursting in to the discussion and saying, "why not just buy a radio at the nearest shop? Do NOT make your own, IT WILL break!" A good advice but completly beside the point.

---

### Post by MadCow108 on 2010-01-19
you just seem to do xor encryption with a constant salted repeatedly md5'ed key

I guess a simple frequency analysis or plaintext attack will do the trick.

---

### Post by Reiger on 2010-01-19
> **MadCow108 said:**
> because of that hashes are considered broken when someone manages what hessies said. Even SHA-1 is cryptographically broken, although its less serious
Being able to generate 2 different versions of a similar but different content and the same hash makes the hash useless as a signature.

What I meant is that MD5 as hashing is still &#8216;working&#8217; for things like file checksums. It is no longer considered cryptographically secure [which is another word for &#8220;so computationally expensive that it is unfeasible to generate input producing a target hash&#8221; but not the same as impossible], but that is something else.

---

### Post by MadCow108 on 2010-01-19
depends on the security level you want.
its not particularly difficult to break md5, especially for file checksums. Its probably harder for password hashes if you limit your input.
All you need is a rack of playstations and a bit of time. Long not unfeasible.
In a few years a pc with one or two GPGPU will probably already do it in a few days.
Its generally advised not to use md5 anymore for security critical applications.

On the other side the broken SHA-1 will still be usable for a few years without too big concern as it requires a lot more computing power.

---

### Post by Hellkeepa on 2010-01-19
HELLo!

Actually... By utilizing the [tunneling attack](http://eprint.iacr.org/2006/105), one can produce a collision to any MD5 hash in under 2 minutes on a laptop from 2006.

Happy codin'!

---

### Post by johnl on 2010-01-19
> **MadCow108 said:**
> you just seem to do xor encryption with a constant salted repeatedly md5'ed key

I guess a simple frequency analysis or plaintext attack will do the trick.

Bingo.


We know that the key repeats every 16 characters.  So every 16th character is XORed with the same value.  Given a long enough input, we can do frequency analysis based on the suspected language, in addition to eliminating ranges of characters from the key value that would decode to 'junk' like high-ascii, control characters, etc.  The cross reference these values between characters encoded with the same key to further reduce the range.

---

### Post by JamesWhisker on 2010-01-19
> **MadCow108 said:**
> you just seem to do xor encryption with a constant salted repeatedly md5'ed key

I guess a simple frequency analysis or plaintext attack will do the trick.
A frequency analysis attack requires a subsitution encryption algoritm. Since this is isn't substitution encryption (every 16 byte round has a new keystream with homogenic probability distribution, since it's a hash function output). But please go on if there's something I missed.

---

### Post by JamesWhisker on 2010-01-19
> **johnl said:**
> Bingo.


We know that the key repeats every 16 characters.  So every 16th character is XORed with the same value.  Given a long enough input, we can do frequency analysis based on the suspected language, in addition to eliminating ranges of characters from the key value that would decode to 'junk' like high-ascii, control characters, etc.  The cross reference these values between characters encoded with the same key to further reduce the range.

Sorry, the keystream doesn't repeat itself. As you can see in the scheme, it takes the output from the last md5 cycle, plus the last encrypted cleartext block and appends it to the input before md5'ing, essentially salting the key.

Now we're getting somewhere though. :)

EDIT:
> **Hellkeepa said:**
> HELLo!

Actually... By utilizing the [tunneling attack]("http://eprint.iacr.org/2006/105"), one can produce a collision to any MD5 hash in under 2 minutes on a laptop from 2006.

Happy codin'!

Sorry, finding MD5 collisions could help you forge certificates but it won't help you if you want to recover cleartext in this algorithm. Anyhow, as stated, if there are some weakness in MD5 that would allow you to attack this encryption scheme, just pretend that it's using SHA1 instead or "the theoretic perfect hashing function".

---

### Post by Senesence on 2010-01-19
Interesting stuff.

I have yet to really look through it in detail, but if anyone else wants to play around with your code (without having to install PHP first), they can do it here:

[http://codepad.org/5GVwfaDw](http://codepad.org/5GVwfaDw)

---

### Post by Hellkeepa on 2010-01-19
HELLo!

**JamesWhisker**: I wasn't making a statement about whether or not your code could be attacked by this, I was merely responding to **MadCow108**'s post above mine. To state that no rack of PS3s are needed, just one 4 year old laptop.

Happy codin'!

---

