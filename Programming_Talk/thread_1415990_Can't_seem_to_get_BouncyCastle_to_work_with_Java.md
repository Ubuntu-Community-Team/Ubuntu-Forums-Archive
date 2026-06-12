---
title: "Can't seem to get BouncyCastle to work with Java"
date: 2010-02-25
forum: Programming Talk
---

### Post by Reneg4d3 on 2010-02-25
Hello Ubuntu community, I am not one to ask for help, rather I look until I find the answer to my problem. However, I am kind of stumped and need some help.

Basically I am trying to compile this java program:
```

import java.security.Security;



import javax.crypto.Cipher;

import javax.crypto.spec.SecretKeySpec;

public class MainClass {

  public static void main(String[] args) throws Exception {

    Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider());        

    byte[] input = " test string ".getBytes();

    byte[] keyBytes = new byte[] { 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09,

        0x0a, 0x0b, 0x0c, 0x0d, 0x0e, 0x0f, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16, 0x17 };



    SecretKeySpec key = new SecretKeySpec(keyBytes, "AES");

    Cipher cipher = Cipher.getInstance("AES/ECB/NoPadding", "BC");

    System.out.println("input text : " + new String(input));

    // encryption pass

    byte[] cipherText = new byte[input.length];

    cipher.init(Cipher.ENCRYPT_MODE, key);

    int ctLength = cipher.update(input, 0, input.length, cipherText, 0);

    ctLength += cipher.doFinal(cipherText, ctLength);

    System.out.println("cipher text: " + new String(cipherText) + " bytes: " + ctLength);

    // decryption pass

    byte[] plainText = new byte[ctLength];

    cipher.init(Cipher.DECRYPT_MODE, key);

    int ptLength = cipher.update(cipherText, 0, ctLength, plainText, 0);

    ptLength += cipher.doFinal(plainText, ptLength);

    System.out.println("plain text : " + new String(plainText) + " bytes: " + ptLength);

  }

}

```When It's done I get the following error:
```

reneg4d3@ubuntu:~/Desktop/BasicSymmetricEncryption/src$ javac MainClass.java
MainClass.java:11: package org.bouncycastle.jce.provider does not exist
    Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider());        
                                                          ^
1 error

```How do I add the package in Ubuntu?
*NOTE* This shows output in JDK 1.6

---

### Post by Some Penguin on 2010-02-25
If you haven't unpacked the jar file right there so that org/bouncycastle/jce/provider is actually a valid directory off of src, you'll want to add the jar file to your CLASSPATH variable.

---

