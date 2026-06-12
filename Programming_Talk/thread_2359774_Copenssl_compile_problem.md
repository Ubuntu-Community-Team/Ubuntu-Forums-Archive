---
title: "C/openssl compile problem"
date: 2017-04-27
forum: Programming Talk
---

### Post by gus_zernial on 2017-04-27
I'm running mlbviewer (https://sourceforge.net/projects/mlbviewer/) on Kubuntu 16.04.2 LTS. This is a python app for baseball. The app itself works, but to watch game video in hi-def one needs a "C" add-on app called "mlbtv-hls-nexdef", which must be downloaded and compiled from source. I did so and the compile fails with the output ....

/tmp/ccIG06Ss.o: In function `mlb_hls_get_and_decrypt':
mlb.c.text+0x1fb8): undefined reference to `EVP_CIPHER_CTX_reset'
mlb.c.text+0x2017): undefined reference to `EVP_CIPHER_CTX_reset'
collect2: error: ld returned 1 exit status
Makefile:11: recipe for target 'mlb' failed

The Makefile is ....

CC=gcc
CFLAGS=-O2
#LIBS=-lm -lcrypto -lpthread -lconfig -lcurl -lhttp_fetcher
LIBS=-lm -lcrypto -lpthread -lconfig -lcurl

mlb = mlb

all: mlb

mlb:
         $(CC) $(CFLAGS) mlb.c utils.c output.c $(LIBS) -o mlbhls

clean:
        rm -f *.o mlbhls

----------------------------------------------------------------------------------
I can't actually find `EVP_CIPHER_CTX_reset' in the source, but I suspect the problem is in function `mlb_hls_get_and_decrypt' here ......

{
                                int lastDecryptLength = 0;

                                EVP_CIPHER_CTX *ctx = EVP_CIPHER_CTX_new();
                                EVP_CIPHER_CTX_init(ctx);

                                if (!master->current_iv || !master->current_aeskey)
                                {
                                        printf("[MLB] Decryption keys NOT SET\n");
                                }
//                              mlb_print_iv(master->current_iv);
//                              mlb_print_aes_key(master->current_aeskey);

                                // Assuming AES128, should check type and set accordingly
                                if (EVP_DecryptInit_ex(ctx, EVP_aes_128_cbc(), NULL, master->current_aeskey->aes_key, master->current_iv->iv) == 1)
                                {
                                        if (EVP_DecryptUpdate(ctx, master->media_out, &out_len, p->write_buf, p->write_pos) == 1)
                                        {
                                                if (EVP_DecryptFinal_ex(ctx, master->media_out + out_len, &lastDecryptLength) == 1)
                                                {
//                                                      printf("[MLB] DBEUG -- Decrypt good: %s (%d)\n", url, out_len + lastDecryptLength);
                                                        ret = out_len + lastDecryptLength;
                                                }
                                                else
                                                {
                                                        printf("[MLB] ERROR!!!!!!!!! BAD DECRYPT [1]\n");
                                                        ret = -1;
                                                }
                                        }
                                }
                                else
                                {
                                        printf("[MLB] ERROR!!!!!!!!! BAD DECRYPT [2]\n");
                                        ret = -2;
                                }
                                EVP_CIPHER_CTX_cleanup(ctx);
                        }


I've installed libssl1.0.0 (1.0.2g-1ubuntu4.6), libconfig9 (1.5-0.2), libcurl3 (7.47.0-1ubuntu2.2), libcurl4-openssl-dev (7.47.0-1ubuntu2.2), libpthread-stubs0-dev (0.3-4), python-pthreading (0.1.4-1).

The C app has been around for a while, and I suspect the problem has to do with version upgrades to openssl which break the C code, but I'm not a developer and I don't know how to fix. Can someone help with diagnosing/fixing?

Thanks, Gus

---

