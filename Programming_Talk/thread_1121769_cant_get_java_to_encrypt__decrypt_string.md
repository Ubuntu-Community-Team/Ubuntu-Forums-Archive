---
title: "cant get java to encrypt / decrypt string"
date: 2009-04-10
forum: Programming Talk
---

### Post by jabibi on 2009-04-10
All I did was use this class i found online
[http://assets.devx.com/sourcecode/10387.zip](http://assets.devx.com/sourcecode/10387.zip)

and this function:


```

private String encode_decode(String str, Integer i) throws EncryptionException{
        //String str is string to encode or decode
        //int i is 1 for encoding or 2 for decoding any other values mess up
        String str2="";
        String encryptionScheme = StringEncrypter.DESEDE_ENCRYPTION_SCHEME;
	String encryptionKey = "type your key here can be alphanumeric";
        StringEncrypter encrypter = new StringEncrypter( encryptionScheme, encryptionKey );
        if(i==1){
            str2=encrypter.encrypt(str);
            //str2 is now the resulting encrypted version of str argument
        }
        if(i==2){
            str2=encrypter.decrypt(str);
            //str2 is now the resulting decrypted version of str argument
        }
        return str2;

```



> Original Title: cant get java to encrypt / decrypt string

Original post:

Hi guys, I need to store some text data in a file but I dont want it to be easily readable for anybody who just opens up a file.

I've searched the web and I've found many programs and examples but all of them work with Byte type instead of string and I wouldnt know how to store a Byte type in a text file correctly

I also found one that returns strings but it uses import on sun.misc.base64encoder / decoder and my netbeans says "import from forbidden library" and for some reason the program just does not work even if I copy / paste it directly from the web without modifying it.

All I want is get some text from a jtextField, encrypt it and make it look like gibberish and put it in a file. And then get the gibberish read from the file and convert it back to the original string.

I've been on this for like a whole week and havent been able to do it. Maybe I'm just a lame programmer hehe.

Thanks.

---

### Post by The Cog on 2009-04-10
You absolutely have to convert the string to a byte array before encrypting, and back again after decrypting. Use String.getBytes("utf8") and new String(bytes, "utf8");

---

### Post by jabibi on 2009-04-11
SOLVED IT, I edited the first message of this thread and posted the what I used as a solution.

Hopefully it will help someone else too.

The Cog, thanks for your advise too.

---

