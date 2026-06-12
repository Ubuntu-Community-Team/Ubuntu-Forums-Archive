---
title: "Help with getting example code running in Java"
date: 2011-04-20
forum: Programming Talk
---

### Post by DBQ on 2011-04-20
Hi everybody. I was trying to run this piece of code from [http://www.java2s.com/Tutorial/Java/0490__Security/BasicRSAexample.htm](http://www.java2s.com/Tutorial/Java/0490__Security/BasicRSAexample.htm)

```

import java.math.BigInteger;
import java.security.KeyFactory;
import java.security.Security;
import java.security.interfaces.RSAPrivateKey;
import java.security.interfaces.RSAPublicKey;
import java.security.spec.RSAPrivateKeySpec;
import java.security.spec.RSAPublicKeySpec;

import javax.crypto.Cipher;

public class MainClass {
  public static void main(String[] args) throws Exception {
    Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider());

    byte[] input = new byte[] { (byte) 0xbe, (byte) 0xef };
    Cipher cipher = Cipher.getInstance("RSA/None/NoPadding", "BC");

    KeyFactory keyFactory = KeyFactory.getInstance("RSA", "BC");
    RSAPublicKeySpec pubKeySpec = new RSAPublicKeySpec(new BigInteger(
        "12345678", 16), new BigInteger("11", 16));
    RSAPrivateKeySpec privKeySpec = new RSAPrivateKeySpec(new BigInteger(
        "12345678", 16), new BigInteger("12345678",
        16));

    RSAPublicKey pubKey = (RSAPublicKey) keyFactory.generatePublic(pubKeySpec);
    RSAPrivateKey privKey = (RSAPrivateKey) keyFactory.generatePrivate(privKeySpec);

    cipher.init(Cipher.ENCRYPT_MODE, pubKey);

    byte[] cipherText = cipher.doFinal(input);
    System.out.println("cipher: " + new String(cipherText));

    cipher.init(Cipher.DECRYPT_MODE, privKey);
    byte[] plainText = cipher.doFinal(cipherText);
    System.out.println("plain : " + new String(plainText));
  }
}

```

I get the following error when I compile it:

```

javac *.java
MainClass.java:13: package org.bouncycastle.jce.provider does not exist
    Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider());

```

Any ideas?

---

### Post by simeon87 on 2011-04-20
Apparently the package 'org.bouncycastle.jce.provider' is missing. If you don't have it on your computer then you'll need to download and add it to the project. Are you running the code from some IDE like Eclipse? If you're running it from the command-line then you need to add the package to your command so Java knows where it is on your computer.

You can do that with -cp:

```
java -cp somejar.jar exampleClass
```

It's not a standard Java package, it's probably made by some external party so it's not surprising that it doesn't exist in a standard Java installation.

---

### Post by NovaAesa on 2011-04-20
It looks like you need the Bouncy Castle libraries installed. Take a look here [http://www.bouncycastle.org/java.html](http://www.bouncycastle.org/java.html)

---

### Post by DBQ on 2011-04-20
Thanks for your replies! Is there a more standard Java library I could use to accomplish my purpose?  I do not want to force my users to install Bouncy Castle.

---

