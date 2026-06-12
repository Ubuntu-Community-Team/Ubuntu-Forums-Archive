---
title: "C++, crypto and MSN..."
date: 2010-07-11
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-07-11
Hi, I'm trying to implement the MSN protocol(MSNP18) in C++ using boost.asio (and generally boost). However there is a specific step in the authentication process that I don't seem to get it right. I am refering to the SSO authentication scheme explained(not entirely) [here](http://msnpiki.msnfanatic.com/index.php/MSNP15:SSO#Computing_the_return_value). I am trying to compute the return value of the first "test value". The result is different. I don't even know if I am doing the right thing or missing something about the bits and bytes :P.

Because the documentation is not really clear about the process, I had as a guide the source of msn-sharp(C#). The relevant source code is [here](http://code.google.com/p/msnp-sharp/source/browse/trunk/MSNPSHARP_DEV/MSNPSharp/SingleSignOn.cs).

The mistake may be in the crypto functions, it may be in the combining of bytes or maybe it is a typo somewhere.

Please take a look in my code and tell me if something is wrong. If you're familiar with MSNP then it would be awesome. Or if you could point to some other source code that works that would be helpful. I just hope you give me a lead... Thanks for your time.

[php]#include <iostream>

#include <string>
#include <cstring>

#include <openssl/sha.h>
#include <openssl/hmac.h>
#include <openssl/evp.h>
#include <openssl/bio.h>
#include <openssl/buffer.h>

struct tagMSGRUSRKEY
{
       unsigned long uStructHeaderSize; // 28. Does not count data
       unsigned long uCryptMode; // CRYPT_MODE_CBC (1)
       unsigned long uCipherType; // TripleDES (0x6603)
       unsigned long uHashType; // SHA1 (0x8004)
       unsigned long uIVLen;    // 8
       unsigned long uHashLen;  // 20
       unsigned long uCipherLen; // 72
// Data
       unsigned char aIVBytes[8];
       unsigned char aHashBytes[20];
       unsigned char aCipherBytes[72];
};

std::string base64Decode(const std::string &data)
{
    BIO *bmem, *b64, *bcontainer;
    
    char *buf = new char[data.size()];
    int decoded_len = 0;
    std::string decoded_data;
    
    // create a memory buffer containing base64 encoded data
    bmem = BIO_new_mem_buf((void*)data.c_str(), data.size());

    //create a base64 filter
    b64 = BIO_new(BIO_f_base64());
    
    // we don't want newlines
    BIO_set_flags(b64, BIO_FLAGS_BASE64_NO_NL);
    
    // push a Base64 filter so that reading from buffer decodes it    
    bcontainer = BIO_push(b64, bmem);

    decoded_len = BIO_read(bcontainer, (void*)buf, data.size());
    BIO_free_all(bcontainer);
    
    decoded_data.assign(buf, decoded_len);
    delete [] buf;
    
    return decoded_data;    
}

std::string base64Encode(const std::string &data)
{
    BIO *bmem, *b64, *bcontainer;
    BUF_MEM *bptr;
    std::string encoded_data;
    
    b64 = BIO_new(BIO_f_base64());
    // we don't want newlines
    BIO_set_flags(b64, BIO_FLAGS_BASE64_NO_NL);
    bmem = BIO_new(BIO_s_mem());
    bcontainer = BIO_push(b64, bmem);
    BIO_write(bcontainer, (void*)data.c_str(), data.size());
    BIO_flush(bcontainer);
    BIO_get_mem_ptr(bcontainer, &bptr);
    
    char *buf = new char[bptr->length];
    memcpy(buf, bptr->data, bptr->length);    
    encoded_data.assign(buf, bptr->length);
    
    delete [] buf;
    BIO_free_all(bcontainer);
    
    return encoded_data;    
}

std::string hmac_hash(const std::string &key, const std::string &magic)
{
    std::string hash;
    unsigned int output_length = 0;
    unsigned char *buf = new unsigned char[EVP_MAX_MD_SIZE];
    
    HMAC(EVP_sha1(), (void*)key.c_str(), key.size(), (unsigned char*)magic.c_str(), magic.size(),
        buf, &output_length);
    
    hash.assign((char*)buf, output_length);
    delete [] buf;
    
    return hash;    
}

std::string derive_key(const std::string &key, const std::string &magic)
{
    std::string hash1, hash2, hash3, hash4, derived_key;
    
    
    hash1 = hmac_hash(key, magic);    
    hash2 = hmac_hash(key, hash1 + magic);
    hash3 = hmac_hash(key, hash1);
    hash4 = hmac_hash(key, hash3 + magic);
    
    derived_key = hash2;
    derived_key.append(hash4, 0, 4);
    
    return key;
}

std::string des3_encrypt(const std::string &key, const std::string &input, const unsigned char *iv)
{
    OpenSSL_add_all_algorithms();
    std::string encrypted_data;    
    unsigned char *buf = new unsigned char[72];
    int output_length = 0;    
    
    EVP_CIPHER_CTX ctx;
    /* Don't set key or IV because we will modify the parameters */
    EVP_CIPHER_CTX_init(&ctx);
    EVP_CipherInit_ex(&ctx, EVP_des_ede3_cbc(), NULL, NULL, NULL, 1);
    EVP_CIPHER_CTX_set_key_length(&ctx, key.size());
    EVP_CIPHER_CTX_set_padding(&ctx, 0);
    /* We finished modifying parameters so now we can set key and IV */
    EVP_CipherInit_ex(&ctx, NULL, NULL, (unsigned char*)key.c_str(), iv, 1);
    EVP_CipherUpdate(&ctx, buf, &output_length, (unsigned char*)input.c_str(), input.size());
    
    encrypted_data.assign((char*)buf, output_length);    
    
    EVP_CipherFinal_ex(&ctx, buf, &output_length);
    encrypted_data.append((char*)buf, output_length);
    
    EVP_CIPHER_CTX_cleanup(&ctx);   
    delete [] buf;
    EVP_cleanup();    
    return encrypted_data;    
}


int main(int argc, char *argv[])
{
    std::string secret = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=";
    std::string nonce = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=";
    unsigned char *iv = new unsigned char[8];
    iv[0] = iv[1] = iv[2] = iv[3] = iv[4] = iv[5] = iv[6] = iv[7] = 0;
    tagMSGRUSRKEY blob;
    
    std::string key1, key2, key3, hash, encrypted_data;
    
    
    key1 = base64Decode(secret);
    key2 = derive_key(key1, "WS-SecureConversationSESSION KEY HASH");
    key3 = derive_key(key1, "WS-SecureConversationSESSION KEY ENCRYPTION");
    hash = hmac_hash(key2, nonce);    
    
    nonce.append(8,'\x08');    
    encrypted_data = des3_encrypt(key3, nonce, iv);
    
    blob.uStructHeaderSize = 28;
    blob.uCryptMode = 1;    
    blob.uCipherType = 0x6603;
    blob.uHashType = 0x8004;
    blob.uIVLen = 8;
    blob.uHashLen = 20;
    blob.uCipherLen = 72;
    
    for (unsigned int i=0; i<8; i++)
    {
        blob.aIVBytes[i] = iv[i];
    }
    
    for (unsigned int i=0; i<hash.size(); i++)
    {
        blob.aHashBytes[i] = hash[i];
    }
    
    for (unsigned int i=0; i<encrypted_data.size(); i++)
    {
        blob.aCipherBytes[i] = encrypted_data[i];
    }
    
    std::string blob_str;
    blob_str.assign(reinterpret_cast<const char*> (&blob), 128);    
    
    std::cout << base64Encode(blob_str) << std::endl;  
    
    delete [] iv;  
    return 0;
}
[/php]

---

### Post by SledgeHammer_999 on 2010-07-11
In the msn-sharp code start looking from line 921.

---

### Post by SledgeHammer_999 on 2010-07-11
Some progress was made. By looking at libpurple's code(libpurple/protocols/msn/nexus.h) I saw that the struct was wrong it uses int's instead of long's. I changed the struct to:

[php]
struct tagMSGRUSRKEY
{
       int uStructHeaderSize; // 28. Does not count data
       int uCryptMode; // CRYPT_MODE_CBC (1)
       int uCipherType; // TripleDES (0x6603)
       int uHashType; // SHA1 (0x8004)
       int uIVLen;    // 8
       int uHashLen;  // 20
       int uCipherLen; // 72
// Data
       char aIVBytes[8];
       char aHashBytes[20];
       char aCipherBytes[72];
};
[/php]

Now the output is correct up to a point(see bold part) the rest is wrong. I suspect that I do something wrong in the base64/endcode-hmac-tripledes functions.
The current output is:
```

**HAAAAAEAAAADZgAABIAAAAgAAAAUAAAASAAAAAAAAAAAAAAA**3KPn7hlQLOgw/IRXIpM3OASRI90qzqh2P4izy8CHEjzkiK4mP6OGRi4eRaUF87KpznEk+75MJD53JgpErPUhwggz5fQhD6B8dB3fXLkQLw8Lj1IOenm8tsdySIg=
```
The correct output should be:
```

HAAAAAEAAAADZgAABIAAAAgAAAAUAAAASAAAAAAAAAAAAAAA7XgT5ohvaZdoXdrWUUcMF2G8OK2JohyYcK5l5MJSitab33scxJeK/RQXcUr0L+R2ZA9CEAzn0izmUzSMp2LZdxSbHtnuxCmptgtoScHp9E26HjQVkA9YJxgK/HM=

```

Also change line **blob_str.assign(reinterpret_cast<const char*> (&blob), 128);** to **blob_str.assign(reinterpret_cast<const char*> (&blob), sizeof(tagMSGRUSRKEY));**

---

### Post by SledgeHammer_999 on 2010-07-15
I solved it. It was a STUPID typo. I can't believe I mislooked it...

In derive_key() replace **return key;** with **return derived_key;**.

---

