---
title: "Enable PHP CRYPT_BLOWFISH hash in Ubuntu"
date: 2013-02-16
forum: Programming Talk
---

### Post by anothertestaccount on 2013-02-16
Hi. Can anyone tell me how can I enable php CRYPT_BLOWFISH hash in Ubuntu? My php version is 5.4.6 and Ubuntu 12.1.

This is what i tried so far
```

<?php
    class ChecksShell extends AppShell
    {
        private function blowfish_hash_example()
        {
            $user='testtesttesttestte';
            $pass='pass';
            
            return 'Blowfish hash example: '.crypt($pass,'$2y$12$'.$user.'$').'\n';
        }

        private function check_hash_algos()
        {
            if(CRYPT_BLOWFISH == 1):
            
                echo 'Blowfish hash is enabled\n';
                echo $this->blowfish_hash_example();

            endif;
        }

        public function main()
        {
            $this->check_hash_algos();
        }
    }

```this returns text unchanged, that is

```

$2y$12$testtesttesttestte$

```Thanks.

---

### Post by SeijiSensei on 2013-02-16
I don't know what you're trying to accomplish, but I use PHP's mcrypt functions for tasks like this:  [http://php.net/manual/en/book.mcrypt.php](http://php.net/manual/en/book.mcrypt.php)

---

### Post by anothertestaccount on 2013-02-16
I am trying to hash passwords.

---

### Post by greenpeace on 2013-02-16
Hi, 
I confess that I don't understand it well, but I've seen that passing a different salt to the function gives different (better) results.

Here's a quick test that I made, loosely based on your code... 

[PHP]<?php
  class CryptTest {

    private function do_crypty_thing() {
        $user  = 'testtesttesttestte';
        $pass  = 'pass';

        $salt1 = '$2y$12$'.$user.'$';
        $salt2 = '!2y!12!'.$user.'!';

        echo "Blowfish hash example 1 with salt ".$salt1.": " . crypt($pass, $salt1) . "\n";
        echo "Blowfish hash example 2 with salt ".$salt2.": " . crypt($pass, $salt2) . "\n";
    }
     
    public function main() {
        return $this->do_crypty_thing();
    }
  }  
  $ct = new CryptTest();
  $ct->main();
?>[/PHP]

and the response from the script:

```
gp@mariachi:~/test$ php crypt.php 
Blowfish hash example 1 with salt $2y$12$testtesttesttestte$: $2y$12$testtesttesttestte$
Blowfish hash example 2 with salt !2y!12!testtesttesttestte!: !2GUKV5zZMaQE
```

Can you change your salt?

Ps. I've done a little more research into the salts, and it's worth taking a look on the 3rd answer to the following question for an explanation: [http://stackoverflow.com/questions/2192354/php-crypt-and-salt-more-clarification-please](http://stackoverflow.com/questions/2192354/php-crypt-and-salt-more-clarification-please)

> it uses a base64 alphabet composed of [a-zA-Z0-9./], with $ as the null (NOT 0) terminating/padding character. If you use any characters outside of that range, or a $ too early, it will either error out or not interpret the entirety of the salt.

hope that helps!
gp

---

### Post by anothertestaccount on 2013-02-17
Thanks, this gets a result. Any workaround for same hashes?

For example if I use salt

```

[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]$user  [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'testtesttesttestte'[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

```

and

```

[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]$user  [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'abcdabcdabcdabcdabcdab'[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

```

I get the same hash.

---

### Post by greenpeace on 2013-02-17
I don't get the same hash here for these salts... try checking your implementation to make sure you don't have any bugs in it.

---

