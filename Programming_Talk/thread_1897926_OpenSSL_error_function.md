---
title: "OpenSSL error function:"
date: 2011-12-20
forum: Programming Talk
---

### Post by spearfish on 2011-12-20
Hi Folks,

I have an OpenSSL programming question for anyone who might be familiar with error-reporting in OpenSSL.  I am working with a program and I can't see what kind of error is happening; I just know that a built-in init function is failing.

There is a built-in library function called EVP_CipherInit_ex() in the file:  evp_enc.c  The purpose of this function (briefly) is: "sets up cipher context ctx for encryption with cipher type from ENGINE impl". 

So basically it is an initialization step used before encrypting.  If initialization can't happen, this function calls an error function called:  EVPerr()

My question is:  Has anyone here used EVPerr?  How do you use it to find out what kind of error has occurred?

thanks!


Below is the OpenSSL code for EVP_CipherInit_ex() which shows how they call EVPerr().  I have a program that calls EVP_CipherInit_ex() that checks the return-code but it does not do anything else to determine what caused the error.  Just checks if the exit code was 0 or not.  I'm trying to add more functionality.  ;)

```
int EVP_CipherInit_ex(EVP_CIPHER_CTX *ctx, const EVP_CIPHER *cipher, ENGINE *impl,
	     const unsigned char *key, const unsigned char *iv, int enc)
	{
	if (enc == -1)
		enc = ctx->encrypt;
	else
		{
		if (enc)
			enc = 1;
		ctx->encrypt = enc;
		}
#ifndef OPENSSL_NO_ENGINE
	/* Whether it's nice or not, "Inits" can be used on "Final"'d contexts
	 * so this context may already have an ENGINE! Try to avoid releasing
	 * the previous handle, re-querying for an ENGINE, and having a
	 * reinitialisation, when it may all be unecessary. */
	if (ctx->engine && ctx->cipher && (!cipher ||
			(cipher && (cipher->nid == ctx->cipher->nid))))
		goto skip_to_init;
#endif
	if (cipher)
		{
		/* Ensure a context left lying around from last time is cleared
		 * (the previous check attempted to avoid this if the same
		 * ENGINE and EVP_CIPHER could be used). */
		EVP_CIPHER_CTX_cleanup(ctx);

		/* Restore encrypt field: it is zeroed by cleanup */
		ctx->encrypt = enc;
#ifndef OPENSSL_NO_ENGINE
		if(impl)
			{
			if (!ENGINE_init(impl))
				{
				EVPerr(EVP_F_EVP_CIPHERINIT_EX, EVP_R_INITIALIZATION_ERROR);
				return 0;
				}
			}
		else
			/* Ask if an ENGINE is reserved for this job */
			impl = ENGINE_get_cipher_engine(cipher->nid);
		if(impl)
			{
			/* There's an ENGINE for this job ... (apparently) */
			const EVP_CIPHER *c = ENGINE_get_cipher(impl, cipher->nid);
			if(!c)
				{
				/* One positive side-effect of US's export
				 * control history, is that we should at least
				 * be able to avoid using US mispellings of
				 * "initialisation"? */
				EVPerr(EVP_F_EVP_CIPHERINIT_EX, EVP_R_INITIALIZATION_ERROR);
				return 0;
				}
			/* We'll use the ENGINE's private cipher definition */
			cipher = c;
			/* Store the ENGINE functional reference so we know
			 * 'cipher' came from an ENGINE and we need to release
			 * it when done. */
			ctx->engine = impl;
			}
		else
			ctx->engine = NULL;
#endif

		ctx->cipher=cipher;
		if (ctx->cipher->ctx_size)
			{
			ctx->cipher_data=OPENSSL_malloc(ctx->cipher->ctx_size);
			if (!ctx->cipher_data)
				{
				EVPerr(EVP_F_EVP_CIPHERINIT_EX, ERR_R_MALLOC_FAILURE);
				return 0;
				}
			}
		else
			{
			ctx->cipher_data = NULL;
			}
		ctx->key_len = cipher->key_len;
		ctx->flags = 0;
		if(ctx->cipher->flags & EVP_CIPH_CTRL_INIT)
			{
			if(!EVP_CIPHER_CTX_ctrl(ctx, EVP_CTRL_INIT, 0, NULL))
				{
				EVPerr(EVP_F_EVP_CIPHERINIT_EX, EVP_R_INITIALIZATION_ERROR);
				return 0;
				}
			}
		}
	else if(!ctx->cipher)
		{
		EVPerr(EVP_F_EVP_CIPHERINIT_EX, EVP_R_NO_CIPHER_SET);
		return 0;
		}
#ifndef OPENSSL_NO_ENGINE
skip_to_init:
#endif
	/* we assume block size is a power of 2 in *cryptUpdate */
	OPENSSL_assert(ctx->cipher->block_size == 1
	    || ctx->cipher->block_size == 8
	    || ctx->cipher->block_size == 16);

	if(!(EVP_CIPHER_CTX_flags(ctx) & EVP_CIPH_CUSTOM_IV)) {
		switch(EVP_CIPHER_CTX_mode(ctx)) {

			case EVP_CIPH_STREAM_CIPHER:
			case EVP_CIPH_ECB_MODE:
			break;

			case EVP_CIPH_CFB_MODE:
			case EVP_CIPH_OFB_MODE:

			ctx->num = 0;
			/* fall-through */

			case EVP_CIPH_CBC_MODE:

			OPENSSL_assert(EVP_CIPHER_CTX_iv_length(ctx) <=
					(int)sizeof(ctx->iv));
			if(iv) memcpy(ctx->oiv, iv, EVP_CIPHER_CTX_iv_length(ctx));
			memcpy(ctx->iv, ctx->oiv, EVP_CIPHER_CTX_iv_length(ctx));
			break;

			default:
			return 0;
			break;
		}
	}

	if(key || (ctx->cipher->flags & EVP_CIPH_ALWAYS_CALL_INIT)) {
		if(!ctx->cipher->init(ctx,key,iv,enc)) return 0;
	}
	ctx->buf_len=0;
	ctx->final_used=0;
	ctx->block_mask=ctx->cipher->block_size-1;
	return 1;
	}
```

---

### Post by spearfish on 2011-12-20
Found the answer:

ERR_get_error(3)

[http://www.openssl.org/docs/crypto/ERR_get_error.html](http://www.openssl.org/docs/crypto/ERR_get_error.html)

---

