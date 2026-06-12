---
title: "newbie with python 3 gnupg module not decrypting text"
date: 2015-04-22
forum: Programming Talk
---

### Post by lance bermudez on 2015-04-22
hello I have a script to encrypt the text and yes that is right i need the text encrypted not the file. it works but the one for decrypting the text does not work right. As to why I'm doing this is because I need to be able to move the file between linux and windows. Also the windows computer is locked you can not install anything but it has python3 on it so I was hoping to be able to use the gnupg module 

Error code in idle is below
```

>>> 
type text 
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1

hQIMA3qClorwwKU+AQ/+L92Mqu1vznqRjVXsnYZJ6Us+LoK+0BVLPcUQJ+XcHA9F
Sq27XfLJvjGYjbvvpuFizNa4PlPb8sXpQ0WtQkYNPzDX2hicY77jL9pIKVxbQiyV
Br2Uy1eDKGEN43fQ8Anw9LveimTWC7SP6LhrVZc/mfvB9GcwcthCx/bpfeWvR4RM
wS/S/hiwf06aYnHw6IvAdUM73kLt7YL1MlQgesofkdH4WfkW1o+ge7W04KP8bl28
Bqnwrbrab0zWz+3npRunU6+8L+GhDPW3X+15paKjhMdk+TGxBGFEDf513z9CjCF1
xG/7TfqYGVNJVHol2wBsgTTrd1xygSA23rdOlzaj7Unny85uXCl9UOwVf50rWoqS
hipEZaRSFOq1nE149Ne1d3BMJ6tK/fApprA6RWlWR9kXq6P+AxAt06ZMTZcrKXCp
2xefLtxP/Gr1hQLyDx3gsPYCCwKSX+1gzB3OFS5SZZe6whyKwQ6817B0Jfb6je5t
lTw907QsNjVXm0xwqBl0VrmUS7rzuPy7AdHPBOwBWVwUz3UsPYjjuE3Vo1iSicc9
nLPp0BD2h30ZTFedcNahM/IsqkL2mQ7Y04a9jlTbqvwHkasMC+xdoMBU4b8HMeyn
F2s8wq3admyl/7yKwKAajoIvITIywYDztfC+0aP9kWLF3j9KTgPpGqJkoz2XkezS
PwEpGBXpZZYpG03S+7IsnkSRVg4H7YDYPhvIvw6gab5fHPkwzOpA7QZKV9zHNPUT
qPD8nr22xB6Fg2Xkm/9bqg==
=J3tC
-----END PGP MESSAGE-----
ok:  False
status:  
stderr:  gpg: WARNING: unsafe permissions on homedir `/home/lance/500gb/ptest/python-gpg/.gnupg'
gpg: no valid OpenPGP data found.
[GNUPG:] NODATA 1
[GNUPG:] NODATA 2
gpg: decrypt_message failed: eof

decrypted string:  b''
>>> ================================ RESTART ================================
>>> 
type text 
hQIMA3qClorwwKU+AQ/+L92Mqu1vznqRjVXsnYZJ6Us+LoK+0BVLPcUQJ+XcHA9F
Sq27XfLJvjGYjbvvpuFizNa4PlPb8sXpQ0WtQkYNPzDX2hicY77jL9pIKVxbQiyV
Br2Uy1eDKGEN43fQ8Anw9LveimTWC7SP6LhrVZc/mfvB9GcwcthCx/bpfeWvR4RM
wS/S/hiwf06aYnHw6IvAdUM73kLt7YL1MlQgesofkdH4WfkW1o+ge7W04KP8bl28
Bqnwrbrab0zWz+3npRunU6+8L+GhDPW3X+15paKjhMdk+TGxBGFEDf513z9CjCF1
xG/7TfqYGVNJVHol2wBsgTTrd1xygSA23rdOlzaj7Unny85uXCl9UOwVf50rWoqS
hipEZaRSFOq1nE149Ne1d3BMJ6tK/fApprA6RWlWR9kXq6P+AxAt06ZMTZcrKXCp
2xefLtxP/Gr1hQLyDx3gsPYCCwKSX+1gzB3OFS5SZZe6whyKwQ6817B0Jfb6je5t
lTw907QsNjVXm0xwqBl0VrmUS7rzuPy7AdHPBOwBWVwUz3UsPYjjuE3Vo1iSicc9
nLPp0BD2h30ZTFedcNahM/IsqkL2mQ7Y04a9jlTbqvwHkasMC+xdoMBU4b8HMeyn
F2s8wq3admyl/7yKwKAajoIvITIywYDztfC+0aP9kWLF3j9KTgPpGqJkoz2XkezS
PwEpGBXpZZYpG03S+7IsnkSRVg4H7YDYPhvIvw6gab5fHPkwzOpA7QZKV9zHNPUT
qPD8nr22xB6Fg2Xkm/9bqg==
=J3tC
ok:  False
status:  
stderr:  gpg: WARNING: unsafe permissions on homedir `/home/lance/500gb/ptest/python-gpg/.gnupg'
gpg: no valid OpenPGP data found.
[GNUPG:] NODATA 1
[GNUPG:] NODATA 2
gpg: decrypt_message failed: eof

decrypted string:  b''

```

my code for decrypting is below and I got it from [http://www.saltycrane.com/blog/2011/10/python-gnupg-gpg-example/](http://www.saltycrane.com/blog/2011/10/python-gnupg-gpg-example/)
```

import gnupg
from pprint import pprint

encrypted_data=input("type text \n")

#text = "a;sdjfla;dfj"

gpg = gnupg.GPG(gnupghome='/home/lance/500gb/ptest/python-gpg/.gnupg')

#always true for home dir permission error
#encrypted_data = gpg.encrypt(text, 'efile', always_trust='true')
#decrypted_data = gpg.decrypt(encrypted_string, passphrase='my passphrase')

encrypted_string = str(encrypted_data)
decrypted_data = gpg.decrypt(encrypted_string, always_trust='ture')

print('ok: ', decrypted_data.ok)
print('status: ', decrypted_data.status)
print('stderr: ', decrypted_data.stderr)
print('decrypted string: ', decrypted_data.data)

```

---

### Post by lance bermudez on 2015-11-10
How do I turn the input into a loop? I found out once be fore but have lost the script.

```

f = ' '

for line in f:
        f = str(input('Copy paste encrypted text here:\n '))

gpg = gnupg.GPG(homedir=r'/home/lance/bin/python/.gnupg')

decrypted_data = gpg.decrypt(f, always_trust='true')

print('ok: ', decrypted_data.ok)
print('status: ', decrypted_data.status)
print('stderr: ', decrypted_data.stderr)
print('decrypted string: ', decrypted_data.data)

```

still getting error
```

Copy paste encrypted text here:
 -----BEGIN PGP MESSAGE-----

Version: GnuPG v1



hQEMAziUAWmp7eEiAQgAlQ1l6G2KHtbVDfyF7mdtt9NUCb75K2FaqLg/Ie/X+XDL

PzwREXkNGrAG2Yrs0cHqFQfIi7O9RjJPVFtrxmWALBBirkVdCza2WpbbnZKAzMGS

6XmF/B4wv4yeu18M73VmMDLJ6+y268Ma/f+VKaMdKjZ/lk59dqO64oAFUQzm+pdQ

LCNrPvTMGsrR8ELeK6PfH9sh1IVyfRqzP0XOZYAenfTg8YXTIUubyP6AoTfnEVcE

5HM1rOawvA+uM10t3vSjHQAp2HoHtDAv+kB19voUuPzE+qJ+xkWM4P65O5Z/v8mD

u9zrhypYwf/a1TwvbIhxYo+oL1OWS7J6dt3QIFY5INJGAfrJCVFL8r5DV8cB1M3p

4vkKPw2xotVBwOHBOwwF1O3j3+Lb80w8/8y4Ud2zvDvFernNicKWozySGI0EGxcm

+oG3r0vTyA==

=4RUa

-----END PGP MESSAGE-----
stderr:  gpg: no valid OpenPGP data found.

[GNUPG:] NODATA 1

[GNUPG:] NODATA 2

gpg: decrypt_message failed: eof


decrypted string:  b''

```

---

