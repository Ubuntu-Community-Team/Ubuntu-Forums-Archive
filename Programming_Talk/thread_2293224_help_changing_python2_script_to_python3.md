---
title: "help changing python2 script to python3"
date: 2015-09-03
forum: Programming Talk
---

### Post by lance bermudez on 2015-09-03
iI have this code from  [https://www.youtube.com/watch?v=lSrrhP2vFS8](https://www.youtube.com/watch?v=lSrrhP2vFS8)
```

 import os, random
from Crypto.Cipher import AES
from Crypto.Hash import SHA256

def encrypt(key, filename):
    chunksize = 64*1024
    outputFile = "(encrypted)"+filename
    filesize = str(os.path.getsize(filename)).zfill(16)
    IV = ''

    for i in range(16):
        IV += chr(random.randint(0, 0xFF))

    encryptor = AES.new(key, AES.MODE_CBC, IV)

    with open(filename, 'rb') as infile:
        with open(outputFile, 'wb') as outfile:
            outfile.write(filesize)
            outfile.write(IV)

            while True:
                chunk = infile.read(chunksize)

                if len(chunk) == 0:
                    break
                elif len(chunk) % 16 != 0:
                    chunk += ' ' * (16 - (len(chunk) %16))

                outfile.write(encryptor.encrypt(chunk))

def decrypt(key, filename):
    chunksize = 64*1024
    outputFile = filename[11:]

    with open(filename, 'rb') as infile:
        filesize = long(infile.read(16))
        IV = infile.read(16)

        decryptor = AES.new(key, AES.MODE_CBC, IV)

        with open(outputFile, 'wb') as outfile:
            while True:
                chunk = infile.read(chunksize)

                if len(chunk) == 0:
                    break

                outfile.write(decryptor.decrypt(chunk))

            outfile.truncate(filesize)

def getKey(password):
    hasher = SHA256.new(password)
    return hasher.digest()

def Main():
    choice = input("Would you like to (E)ncrypt or (D)ecrypt?: ")

    if choice == 'E':
        filename = input("File to encrypt: ")
        password = input("Password: ").encode('utf-8')
        encrypt(getKey(password), filename)
        print("Done")
    if choice == 'D':
        filename = input("File to decrypt: ")
        password = input("Password: ")
        decrypt(getKey(password), filename)
        print("Done")
    else:
        print("No option selected, closing...")

if __name__== '__main__':
    Main()

```

error I get is
```

Would you like to (E)ncrypt or (D)ecrypt?: E
File to encrypt: test.txt
Password: test
Traceback (most recent call last):
  File "G:\tester\encrypt.py", line 77, in <module>
    Main()
  File "G:\tester\encrypt.py", line 66, in Main
    encrypt(getKey(password), filename)
  File "G:\tester\encrypt.py", line 18, in encrypt
    encryptor = AES.new(key, AES.MODE_CBC, IV)
  File "C:\Python34\lib\site-packages\pycrypto-2.6.1-py3.4-win32.egg\Crypto\Cipher\AES.py", line 95, in new
    return AESCipher(key, *args, **kwargs)
  File "C:\Python34\lib\site-packages\pycrypto-2.6.1-py3.4-win32.egg\Crypto\Cipher\AES.py", line 59, in __init__
    blockalgo.BlockAlgo.__init__(self, _AES, key, *args, **kwargs)
  File "C:\Python34\lib\site-packages\pycrypto-2.6.1-py3.4-win32.egg\Crypto\Cipher\blockalgo.py", line 141, in __init__
    self._cipher = factory.new(key, *args, **kwargs)
ValueError: IV must be 16 bytes long

```

---

### Post by Vaphell on 2015-09-03
```

#!/usr/bin/env python3


import os
from Crypto.Cipher import AES
from Crypto.Hash   import SHA256
from Crypto        import Random



def encrypt(key, filename):
    chunksize = 64*1024
    outputFile = "(encrypted)"+filename
    filesize = '{:016d}'.format(os.path.getsize(filename)).encode('utf-8')
    IV = Random.new().read(16)

    encryptor = AES.new(key, AES.MODE_CBC, IV)

    with open(filename, 'rb') as infile:
        with open(outputFile, 'wb') as outfile:
            outfile.write(filesize)
            outfile.write(IV)

            while True:
                chunk = infile.read(chunksize)
                if len(chunk) == 0:
                    break
                elif len(chunk) % 16 != 0:
                    chunk += b' ' * (16 - (len(chunk) %16))

                outfile.write(encryptor.encrypt(chunk))




def decrypt(key, filename):
    chunksize = 64*1024
    outputFile = filename[11:]

    with open(filename, 'rb') as infile:
        filesize = int(infile.read(16).decode('utf-8'))
        IV = infile.read(16)

        decryptor = AES.new(key, AES.MODE_CBC, IV)

        with open(outputFile, 'wb') as outfile:
            while True:
                chunk = infile.read(chunksize)

                if len(chunk) == 0:
                    break

                outfile.write(decryptor.decrypt(chunk))

            outfile.truncate(filesize)

def getKey(password):
    password = password.encode('utf-8')
    hasher = SHA256.new(password)
    return hasher.digest()

def Main():   
    choice = input("Would you like to (E)ncrypt or (D)ecrypt?: ")

    if choice.upper() == 'E':
        filename = input("File to encrypt: ")
        password = input("Password: ")
        encrypt(getKey(password), filename)
        print("Done")
    elif choice.upper() == 'D':
        filename = input("File to decrypt: ")
        password = input("Password: ")
        decrypt(getKey(password), filename)
        print("Done")
    else:
        print("No option selected, closing...")

if __name__== '__main__':
    Main()
```

encoding/decoding to switch between str in utf-8 and bytes, also changed the way IV is generated.

---

### Post by lance bermudez on 2015-09-06
Thank you Vaphell, that works.

---

