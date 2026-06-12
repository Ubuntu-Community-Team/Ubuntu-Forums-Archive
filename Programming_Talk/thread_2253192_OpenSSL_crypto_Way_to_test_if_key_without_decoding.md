---
title: "OpenSSL crypto: Way to test if key without decoding?"
date: 2014-11-17
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-11-17
So I'm checking out some of the free crypto libraries on Linux ( finally ) and spent the day figuring out how to using OpenSSL, and with the help of some example code I got what I wanted up and running... Which was just to take a alphanumeric password to turn into the key and iv for AES.

The one thing I was hoping/expecting to happen though, is that if I entered the wrong key, that OpenSSL would do some kind of automatic error checking and exit gracefully instead of trying to decrypt the information with the wrong values.  It apparently does not do this ( or at least I haven't seen anything about a function for it so far ) so I'm getting the idea I'll have to devise my own method.

I was thinking of just putting a byte or two at the header of the file, something unique like a magic number that I could decode first, test, and then if it wasn't what was expected I could make the program fail gracefully telling me a nice "Password incorrect".  But I feel like this is a clumsy way to do it and that there's probably a better way I don't know about.

This is the code I'm working on so far...  Just the barebones to get it started.  Syntax is program password infile outfile [-e|-d]

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <openssl/evp.h>

int main(int argc, char *argv[])
{
    const EVP_CIPHER *cipher;
    const EVP_MD *dgst = NULL;
    unsigned char key[EVP_MAX_KEY_LENGTH], iv[EVP_MAX_IV_LENGTH];
    const char *password = argv[1];
    const unsigned char *salt = NULL;
    int i;

    FILE *in = fopen(argv[2],"rb");
    FILE *out = fopen(argv[3],"wb");

    OpenSSL_add_all_algorithms();

    cipher = EVP_get_cipherbyname("aes-256-cbc");
    if(!cipher) { fprintf(stderr, "no such cipher\n"); return 1; }

    dgst=EVP_get_digestbyname("md5");
    if(!dgst) { fprintf(stderr, "no such digest\n"); return 1; }

    if(!EVP_BytesToKey(cipher, dgst, salt,
        (unsigned char *) password,
        strlen(password), 1, key, iv))
    {
        fprintf(stderr, "EVP_BytesToKey failed\n");
        return 1;
    }

    printf("Key: "); for(i=0; i<cipher->key_len; ++i) { printf("%02x", key[i]); } printf("\n");
    printf("IV: "); for(i=0; i<cipher->iv_len; ++i) { printf("%02x", iv[i]); } printf("\n");

    if(argv[4][1] == 'e')
      {
	encrypt(in,out,key,iv);
      }
    else if(argv[4][1] == 'd')
	{
	  decrypt(in,out,key,iv);
	}

	       fclose(in);
	       fclose(out);

    return 0;
}

int encrypt(FILE *in, FILE *out, unsigned char *key, unsigned char *iv)
{
  /* Allow enough space in output buffer for additional block */
  unsigned char inbuf[1024], outbuf[1024 + EVP_MAX_BLOCK_LENGTH];
  int inlen, outlen, tlen;
  EVP_CIPHER_CTX ctx;
  EVP_CIPHER_CTX_init(&ctx);
  EVP_EncryptInit_ex(&ctx, EVP_aes_256_cbc(),NULL, key, iv);

  for(;;)
    {
      inlen = fread(inbuf, 1, 1024, in);
      if(inlen <= 0) break;
      if(!EVP_EncryptUpdate(&ctx, outbuf, &outlen, inbuf, inlen))
	{
	  /* Error */
	  EVP_CIPHER_CTX_cleanup(&ctx);
	  return 0;
	}
      fwrite(outbuf, 1, outlen, out);
    }
  if(!EVP_EncryptFinal_ex(&ctx, outbuf,&outlen ))
    {
      /* Error */
      EVP_CIPHER_CTX_cleanup(&ctx);
      return 0;
    }
  fwrite(outbuf, 1, outlen, out);
  EVP_CIPHER_CTX_cleanup(&ctx);
  return 1;
}

int decrypt(FILE *in, FILE *out, unsigned char *key, unsigned char *iv)
{
  /* Allow enough space in output buffer for additional block */
  unsigned char inbuf[1024], outbuf[1024 + EVP_MAX_BLOCK_LENGTH];
  int inlen, outlen, tlen;
  EVP_CIPHER_CTX ctx;
  EVP_CIPHER_CTX_init(&ctx);
  EVP_DecryptInit(&ctx, EVP_aes_256_cbc(), key, iv);

  for(;;)
    {
      inlen = fread(inbuf, 1, 1024, in);
      if(inlen <= 0) break;
      if(!EVP_DecryptUpdate(&ctx, outbuf, &outlen, inbuf, inlen))
	{
	  /* Error */
	  EVP_CIPHER_CTX_cleanup(&ctx);
	  return 0;
	}
      fwrite(outbuf, 1, outlen, out);
    }
  if(!EVP_DecryptFinal_ex(&ctx, outbuf,&outlen ))
    {
      /* Error */
      EVP_CIPHER_CTX_cleanup(&ctx);
      return 0;
    }
  fwrite(outbuf, 1, outlen, out);
  EVP_CIPHER_CTX_cleanup(&ctx);
  return 1;
}

```

---

### Post by ofnuts on 2014-11-18
Assuming you use two bytes (65536 values): if you have the wrong key, you will be generating a random value from these two bytes. This will give you one chance out of 65536 to think that the key is good when it is not... So, not a bad idea to check the key is bad, but best check a lot more bytes to ensure the key is good... 

If you want something really robust, have the data contain the payload and a hash of the payload. After decryption (that you can stop early if you use the technique above), recompute the hash of the payload and compare it to the hash you extracted from the decrypted file.

---

### Post by SagaciousKJB on 2014-11-19
I like that idea of hashing.  The only thing is I'm not really sure how I would go about putting the hash in the file, and then not having the encryption/decryption routines read the hash as part of the payload.  I suppose if the hash were a constant length, I could advance the file stream by that many bytes *before* beginning any encryption/decryption routines, and then write the new hash to the beginning of a file to contain both the hash and the payload?

Beyond that, I understand hashes are supposed to be one-way, but is there any security flaw in putting the hash in the file?

I also am not familiar with any hashing functions.  Are there standard ones available?  Particularly one that will read a file instead of a buffer in memory.

---

### Post by ofnuts on 2014-11-19
The hash has to be encrypted too... then you check the hash of the decrypted against the decrypted hash. The chances that a wrongly decrypted hash ends up being the hash of wrongly encrypted data are very,very, small (2**256 or more, depending on the hash algorithm used).

---

### Post by SagaciousKJB on 2014-11-21
I've heard of generating something called a MAC based on the IV?  I noticed a function in the OpenSSL lib for this ( can't find it right at this second but I remember it being there somewhere).

Anyway, I thought I would be "smart" by just appending the IV itself to the end of the file, then encrypting it.  That way when I decrypted the file, I could just check the IV against the IV that was generated by the supplied password and KeyToBytes() function, but for whatever reason in my code it would always read the IV from the file incorrectly and cause a false-positive for the password being incorrect--I didn't like the idea of writing the IV to the file anyway but just wanted to see if it would work.  Clearly I don't know how to properly write a code to do this, but figure I should learn the right functions to figure it out with at first.

---

