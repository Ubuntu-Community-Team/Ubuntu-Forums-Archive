---
title: "Issue with OpenSSL commands and PHP.. Please help"
date: 2013-03-06
forum: Programming Talk
---

### Post by KingNeil on 2013-03-06
I am using OpenSSL, in order to encrypt a string.... using AES-256, and using the password, "password".

In an SH file, I have the following:

```
echo -n "string goes here" | openssl aes-256-cbc -a -out file.enc -pass pass:password
```

I run the SH file with sh file.sh ... and it works fine....

Now, note... the string that I am encrypting is very long... it's 355,272 characters, to be precise... and so, I won't clog up this forum by typing it out... but you can imagine how long that is...

So, see... when I encrypt the long string using sh file.sh ... it works

But, see... I am trying to have this command run from within a PHP script

And so.... In PHP..... I do:

```
$thecommand = "echo -n "string goes here" | openssl aes-256-cbc -a -out file.enc -pass pass:password"
$return = shell_exec($thecommand);
```

And.... when I run this in PHP, it simply does not work.... however, if I encrypt a string with less characters.. it DOES work... and so.... PHP is running into a problem, because the length of the string is too long....

And thus, I was wondering....is there a way to get around this problem..? is there a setting in PHP.... or could I pipe in the string gradually... and OpenSSL does it piece by piece..?

Or... am I just going to have to split up the string into pieces, encrypt each piece, and then put them back together again after they have been decrypted?

Thanks....

---

### Post by SeijiSensei on 2013-03-06
I'd use the mcrypt functions in PHP for this task.

First, install the "[php5-mcrypt](http://packages.ubuntu.com/precise/php5-mcrypt)" package and restart Apache.

You want to use the "MCRYPT_RIJNDAEL_256" cipher for 256-bit AES.

I once needed to write a couple of PHP functions to encrypt a string and store it in a database.  I chose AES256 to do the encryption, then used Base64 encoding to create a nice plain-text string that can be stored in a character field.  Here are the functions I wrote; you're welcome to them:

```

    function b64_encrypt($string,$key) {

        # encrypt a string with Rijndael-256 and $key
        # return the base64 encoding of the encrypted result

        # from the PHP manual
        $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
        $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
        mcrypt_generic_init($td, $key, $iv);

        # added base64 encoding here
        $encrypted_data = base64_encode(mcrypt_generic($td, $string));

        mcrypt_generic_deinit($td);
        mcrypt_module_close($td);

        return $encrypted_data;

    }


    function b64_decrypt($string,$key) {

        # convert a base-64 encoded string into a Rijndael-256
        # cipher then decrypt using $key

        $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
        $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
        mcrypt_generic_init($td, $key, $iv);

        $decrypted_data = mdecrypt_generic($td, base64_decode($string));

        mcrypt_generic_deinit($td);
        mcrypt_module_close($td);

        # trim any padding
        return trim($decrypted_data);

    }

```

---

### Post by KingNeil on 2013-03-06
Thanks for the useful reply, but there's a good reason I need to use shell_exec and OpenSSL

Regardless, I just split the string into chunks, and then ran OpenSSL on each chunk, and then decrypted it on the other side, and pieced the chunks back together again.

And so, I basically answered my own question. 

Thanks anyway. I'm sure your script may end up being useful for someone else.

---

