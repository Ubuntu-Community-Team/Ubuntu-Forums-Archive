---
title: "Python gpgme: &quot;gpg -c&quot;"
date: 2014-02-28
forum: Programming Talk
---

### Post by kumoshk on 2014-02-28
With GNU Privacy Guard, you can type
```

gpg -c myFile

```

from the command-line. Then, it prompts you for a passphrase and creates a gpg file. To decrypt the file, you can type:
```

gpg myFile.gpg

```

and it decrypts it. Pretty simple. No messing with keys (from the user's viewpoint, at least).

I'm wanting to do the same thing in Python with pygpgme, version 0.3, which is the current version (in Ubuntu in Synaptic, it's called python-gpgme; you import gpgme rather than pygpgme, though).

Any idea how?

I don't want to mess around with keys and stuff. This isn't for email or anything like that. It's just for password-protecting files on a personal computer (without regard to the Internet).

Anyway, I know the solution may involve
```

gpgme.Context.encrypt()

```

as that does support symmetric encryption, somehow. I just don't know how. I'm still searching for the documentation. However, gpgme.Context.encrypt() takes four parameters, beginning with a list, followed by an int, followed by two other things (the content and the cipher, respectively) that can at least sometimes be io.BytesIO objects.

Due to the lack of known documentation, I'll give you some of the attributes of the objects involved with the gpgme module, for reference (using dir() to discover them):
```

>> dir(gpgme)
['Context', 'DATA_ENCODING_ARMOR', 'DATA_ENCODING_BASE64', 'DATA_ENCODING_BINARY', 'DATA_ENCODING_NONE', 'ENCRYPT_ALWAYS_TRUST', 'ERR_AGENT', 'ERR_AMBIGUOUS_NAME', 'ERR_ASSUAN', 'ERR_ASSUAN_SERVER_FAULT', 'ERR_BAD_BER', 'ERR_BAD_CA_CERT', 'ERR_BAD_CERT', 'ERR_BAD_CERT_CHAIN', 'ERR_BAD_DATA', 'ERR_BAD_KEY', 'ERR_BAD_MPI', 'ERR_BAD_PASSPHRASE', 'ERR_BAD_PIN', 'ERR_BAD_PIN_METHOD', 'ERR_BAD_PUBKEY', 'ERR_BAD_SECKEY', 'ERR_BAD_SIGNATURE', 'ERR_BAD_URI', 'ERR_BUFFER_TOO_SHORT', 'ERR_BUG', 'ERR_CANCELED', 'ERR_CARD', 'ERR_CARD_NOT_INITIALIZED', 'ERR_CARD_NOT_PRESENT', 'ERR_CARD_REMOVED', 'ERR_CARD_RESET', 'ERR_CERT_EXPIRED', 'ERR_CERT_REVOKED', 'ERR_CERT_TOO_YOUNG', 'ERR_CHECKSUM', 'ERR_CIPHER_ALGO', 'ERR_COMPR_ALGO', 'ERR_CONFIGURATION', 'ERR_CONFLICT', 'ERR_CORRUPTED_PROTECTION', 'ERR_CRL_TOO_OLD', 'ERR_DECRYPT_FAILED', 'ERR_DIGEST_ALGO', 'ERR_DIRMNGR', 'ERR_DUP_VALUE', 'ERR_E2BIG', 'ERR_EACCES', 'ERR_EADDRINUSE', 'ERR_EADDRNOTAVAIL', 'ERR_EADV', 'ERR_EAFNOSUPPORT', 'ERR_EAGAIN', 'ERR_EALREADY', 'ERR_EAUTH', 'ERR_EBACKGROUND', 'ERR_EBADE', 'ERR_EBADF', 'ERR_EBADFD', 'ERR_EBADMSG', 'ERR_EBADR', 'ERR_EBADRPC', 'ERR_EBADRQC', 'ERR_EBADSLT', 'ERR_EBFONT', 'ERR_EBUSY', 'ERR_ECANCELED', 'ERR_ECHILD', 'ERR_ECHRNG', 'ERR_ECOMM', 'ERR_ECONNABORTED', 'ERR_ECONNREFUSED', 'ERR_ECONNRESET', 'ERR_ED', 'ERR_EDEADLK', 'ERR_EDEADLOCK', 'ERR_EDESTADDRREQ', 'ERR_EDIED', 'ERR_EDOM', 'ERR_EDOTDOT', 'ERR_EDQUOT', 'ERR_EEXIST', 'ERR_EFAULT', 'ERR_EFBIG', 'ERR_EFTYPE', 'ERR_EGRATUITOUS', 'ERR_EGREGIOUS', 'ERR_EHOSTDOWN', 'ERR_EHOSTUNREACH', 'ERR_EIDRM', 'ERR_EIEIO', 'ERR_EILSEQ', 'ERR_EINPROGRESS', 'ERR_EINTR', 'ERR_EINVAL', 'ERR_EIO', 'ERR_EISCONN', 'ERR_EISDIR', 'ERR_EISNAM', 'ERR_EL2HLT', 'ERR_EL2NSYNC', 'ERR_EL3HLT', 'ERR_EL3RST', 'ERR_ELEMENT_NOT_FOUND', 'ERR_ELIBACC', 'ERR_ELIBBAD', 'ERR_ELIBEXEC', 'ERR_ELIBMAX', 'ERR_ELIBSCN', 'ERR_ELNRNG', 'ERR_ELOOP', 'ERR_EMEDIUMTYPE', 'ERR_EMFILE', 'ERR_EMLINK', 'ERR_EMSGSIZE', 'ERR_EMULTIHOP', 'ERR_ENAMETOOLONG', 'ERR_ENAVAIL', 'ERR_ENCODING_PROBLEM', 'ERR_ENEEDAUTH', 'ERR_ENETDOWN', 'ERR_ENETRESET', 'ERR_ENETUNREACH', 'ERR_ENFILE', 'ERR_ENOANO', 'ERR_ENOBUFS', 'ERR_ENOCSI', 'ERR_ENODATA', 'ERR_ENODEV', 'ERR_ENOENT', 'ERR_ENOEXEC', 'ERR_ENOLCK', 'ERR_ENOLINK', 'ERR_ENOMEDIUM', 'ERR_ENOMEM', 'ERR_ENOMSG', 'ERR_ENONET', 'ERR_ENOPKG', 'ERR_ENOPROTOOPT', 'ERR_ENOSPC', 'ERR_ENOSR', 'ERR_ENOSTR', 'ERR_ENOSYS', 'ERR_ENOTBLK', 'ERR_ENOTCONN', 'ERR_ENOTDIR', 'ERR_ENOTEMPTY', 'ERR_ENOTNAM', 'ERR_ENOTSOCK', 'ERR_ENOTSUP', 'ERR_ENOTTY', 'ERR_ENOTUNIQ', 'ERR_ENXIO', 'ERR_EOF', 'ERR_EOF_GCRYPT', 'ERR_EOPNOTSUPP', 'ERR_EOVERFLOW', 'ERR_EPERM', 'ERR_EPFNOSUPPORT', 'ERR_EPIPE', 'ERR_EPROCLIM', 'ERR_EPROCUNAVAIL', 'ERR_EPROGMISMATCH', 'ERR_EPROGUNAVAIL', 'ERR_EPROTO', 'ERR_EPROTONOSUPPORT', 'ERR_EPROTOTYPE', 'ERR_ERANGE', 'ERR_EREMCHG', 'ERR_EREMOTE', 'ERR_EREMOTEIO', 'ERR_ERESTART', 'ERR_EROFS', 'ERR_ERPCMISMATCH', 'ERR_ESHUTDOWN', 'ERR_ESOCKTNOSUPPORT', 'ERR_ESPIPE', 'ERR_ESRCH', 'ERR_ESRMNT', 'ERR_ESTALE', 'ERR_ESTRPIPE', 'ERR_ETIME', 'ERR_ETIMEDOUT', 'ERR_ETOOMANYREFS', 'ERR_ETXTBSY', 'ERR_EUCLEAN', 'ERR_EUNATCH', 'ERR_EUSERS', 'ERR_EWOULDBLOCK', 'ERR_EXDEV', 'ERR_EXFULL', 'ERR_GENERAL', 'ERR_HARDWARE', 'ERR_IDENTIFIER_NOT_FOUND', 'ERR_INCOMPLETE_LINE', 'ERR_INTERNAL', 'ERR_INV_ARG', 'ERR_INV_ARMOR', 'ERR_INV_ATTR', 'ERR_INV_BER', 'ERR_INV_CARD', 'ERR_INV_CERT_OBJ', 'ERR_INV_CIPHER_MODE', 'ERR_INV_CMS_OBJ', 'ERR_INV_CRL', 'ERR_INV_CRL_OBJ', 'ERR_INV_DATA', 'ERR_INV_ENGINE', 'ERR_INV_FLAG', 'ERR_INV_HANDLE', 'ERR_INV_ID', 'ERR_INV_INDEX', 'ERR_INV_KEYINFO', 'ERR_INV_KEYLEN', 'ERR_INV_KEYRING', 'ERR_INV_LENGTH', 'ERR_INV_MAC', 'ERR_INV_NAME', 'ERR_INV_OBJ', 'ERR_INV_OID_STRING', 'ERR_INV_OP', 'ERR_INV_PACKET', 'ERR_INV_PARAMETER', 'ERR_INV_PASSPHRASE', 'ERR_INV_REQUEST', 'ERR_INV_RESPONSE', 'ERR_INV_SESSION_KEY', 'ERR_INV_SEXP', 'ERR_INV_STATE', 'ERR_INV_TAG', 'ERR_INV_TIME', 'ERR_INV_URI', 'ERR_INV_USER_ID', 'ERR_INV_VALUE', 'ERR_KEYRING_OPEN', 'ERR_KEYSERVER', 'ERR_KEY_EXPIRED', 'ERR_LINE_TOO_LONG', 'ERR_LOCALE_PROBLEM', 'ERR_MISSING_ACTION', 'ERR_MISSING_CERT', 'ERR_MISSING_VALUE', 'ERR_MODULE_NOT_FOUND', 'ERR_NETWORK', 'ERR_NOTHING_FOUND', 'ERR_NOT_CONFIRMED', 'ERR_NOT_DER_ENCODED', 'ERR_NOT_ENCRYPTED', 'ERR_NOT_FOUND', 'ERR_NOT_IMPLEMENTED', 'ERR_NOT_LOCKED', 'ERR_NOT_PROCESSED', 'ERR_NOT_SUPPORTED', 'ERR_NOT_TRUSTED', 'ERR_NO_AGENT', 'ERR_NO_CMS_OBJ', 'ERR_NO_CRL_KNOWN', 'ERR_NO_DATA', 'ERR_NO_DIRMNGR', 'ERR_NO_ENCODING_METHOD', 'ERR_NO_ENCRYPTION_SCHEME', 'ERR_NO_ERROR', 'ERR_NO_OBJ', 'ERR_NO_PIN_ENTRY', 'ERR_NO_PKCS15_APP', 'ERR_NO_POLICY_MATCH', 'ERR_NO_PRIME', 'ERR_NO_PUBKEY', 'ERR_NO_SCDAEMON', 'ERR_NO_SECKEY', 'ERR_NO_SIGNATURE_SCHEME', 'ERR_NO_USER_ID', 'ERR_NO_VALUE', 'ERR_PIN_BLOCKED', 'ERR_PIN_ENTRY', 'ERR_PIN_NOT_SYNCED', 'ERR_PROTOCOL_VIOLATION', 'ERR_PUBKEY_ALGO', 'ERR_PUBKEY_NOT_TRUSTED', 'ERR_RESOURCE_LIMIT', 'ERR_SCDAEMON', 'ERR_SELFTEST_FAILED', 'ERR_SEXP_BAD_CHARACTER', 'ERR_SEXP_BAD_HEX_CHAR', 'ERR_SEXP_BAD_OCT_CHAR', 'ERR_SEXP_BAD_QUOTATION', 'ERR_SEXP_INV_LEN_SPEC', 'ERR_SEXP_NESTED_DH', 'ERR_SEXP_NOT_CANONICAL', 'ERR_SEXP_ODD_HEX_NUMBERS', 'ERR_SEXP_STRING_TOO_LONG', 'ERR_SEXP_UNEXPECTED_PUNC', 'ERR_SEXP_UNMATCHED_DH', 'ERR_SEXP_UNMATCHED_PAREN', 'ERR_SEXP_ZERO_PREFIX', 'ERR_SIG_CLASS', 'ERR_SIG_EXPIRED', 'ERR_SOURCE_DIRMNGR', 'ERR_SOURCE_GCRYPT', 'ERR_SOURCE_GPG', 'ERR_SOURCE_GPGAGENT', 'ERR_SOURCE_GPGME', 'ERR_SOURCE_GPGSM', 'ERR_SOURCE_GSTI', 'ERR_SOURCE_KEYBOX', 'ERR_SOURCE_KSBA', 'ERR_SOURCE_PINENTRY', 'ERR_SOURCE_SCD', 'ERR_SOURCE_UNKNOWN', 'ERR_SOURCE_USER_1', 'ERR_SOURCE_USER_2', 'ERR_SOURCE_USER_3', 'ERR_SOURCE_USER_4', 'ERR_SYNTAX', 'ERR_TIMEOUT', 'ERR_TIME_CONFLICT', 'ERR_TOO_LARGE', 'ERR_TOO_SHORT', 'ERR_TRIBUTE_TO_D_A', 'ERR_TRUNCATED', 'ERR_TRUSTDB', 'ERR_UNEXPECTED', 'ERR_UNEXPECTED_TAG', 'ERR_UNKNOWN_ALGORITHM', 'ERR_UNKNOWN_CMS_OBJ', 'ERR_UNKNOWN_ERRNO', 'ERR_UNKNOWN_HOST', 'ERR_UNKNOWN_NAME', 'ERR_UNKNOWN_PACKET', 'ERR_UNKNOWN_SEXP', 'ERR_UNKNOWN_VERSION', 'ERR_UNSUPPORTED_ALGORITHM', 'ERR_UNSUPPORTED_CERT', 'ERR_UNSUPPORTED_CMS_OBJ', 'ERR_UNSUPPORTED_CMS_VERSION', 'ERR_UNSUPPORTED_CRL_VERSION', 'ERR_UNSUPPORTED_ENCODING', 'ERR_UNSUPPORTED_OPERATION', 'ERR_UNSUPPORTED_PROTECTION', 'ERR_UNSUPPORTED_PROTOCOL', 'ERR_UNUSABLE_PUBKEY', 'ERR_UNUSABLE_SECKEY', 'ERR_USER_1', 'ERR_USER_10', 'ERR_USER_11', 'ERR_USER_12', 'ERR_USER_13', 'ERR_USER_14', 'ERR_USER_15', 'ERR_USER_16', 'ERR_USER_2', 'ERR_USER_3', 'ERR_USER_4', 'ERR_USER_5', 'ERR_USER_6', 'ERR_USER_7', 'ERR_USER_8', 'ERR_USER_9', 'ERR_USE_CONDITIONS', 'ERR_VALUE_NOT_FOUND', 'ERR_WEAK_KEY', 'ERR_WRONG_BLOB_TYPE', 'ERR_WRONG_CARD', 'ERR_WRONG_KEY_USAGE', 'ERR_WRONG_PUBKEY_ALGO', 'ERR_WRONG_SECKEY', 'GenkeyResult', 'GpgmeError', 'IMPORT_NEW', 'IMPORT_SECRET', 'IMPORT_SIG', 'IMPORT_SUBKEY', 'IMPORT_UID', 'ImportResult', 'KEYLIST_MODE_EXTERN', 'KEYLIST_MODE_LOCAL', 'KEYLIST_MODE_SIGS', 'KEYLIST_MODE_VALIDATE', 'Key', 'KeyIter', 'KeySig', 'MD_CRC24_RFC2440', 'MD_CRC32', 'MD_CRC32_RFC1510', 'MD_HAVAL', 'MD_MD2', 'MD_MD4', 'MD_MD5', 'MD_NONE', 'MD_RMD160', 'MD_SHA1', 'MD_SHA256', 'MD_SHA384', 'MD_SHA512', 'MD_TIGER', 'NewSignature', 'PK_DSA', 'PK_ELG', 'PK_ELG_E', 'PK_RSA', 'PK_RSA_E', 'PK_RSA_S', 'PROTOCOL_CMS', 'PROTOCOL_OpenPGP', 'SIGSUM_BAD_POLICY', 'SIGSUM_CRL_MISSING', 'SIGSUM_CRL_TOO_OLD', 'SIGSUM_GREEN', 'SIGSUM_KEY_EXPIRED', 'SIGSUM_KEY_MISSING', 'SIGSUM_KEY_REVOKED', 'SIGSUM_RED', 'SIGSUM_SIG_EXPIRED', 'SIGSUM_SYS_ERROR', 'SIGSUM_VALID', 'SIG_MODE_CLEAR', 'SIG_MODE_DETACH', 'SIG_MODE_NORMAL', 'STATUS_ABORT', 'STATUS_ALREADY_SIGNED', 'STATUS_BADARMOR', 'STATUS_BADMDC', 'STATUS_BADSIG', 'STATUS_BAD_PASSPHRASE', 'STATUS_BEGIN_DECRYPTION', 'STATUS_BEGIN_ENCRYPTION', 'STATUS_BEGIN_STREAM', 'STATUS_DECRYPTION_FAILED', 'STATUS_DECRYPTION_OKAY', 'STATUS_DELETE_PROBLEM', 'STATUS_ENC_TO', 'STATUS_END_DECRYPTION', 'STATUS_END_ENCRYPTION', 'STATUS_END_STREAM', 'STATUS_ENTER', 'STATUS_EOF', 'STATUS_ERRMDC', 'STATUS_ERROR', 'STATUS_ERRSIG', 'STATUS_EXPKEYSIG', 'STATUS_EXPSIG', 'STATUS_FILE_DONE', 'STATUS_FILE_ERROR', 'STATUS_FILE_START', 'STATUS_GET_BOOL', 'STATUS_GET_HIDDEN', 'STATUS_GET_LINE', 'STATUS_GOODMDC', 'STATUS_GOODSIG', 'STATUS_GOOD_PASSPHRASE', 'STATUS_GOT_IT', 'STATUS_IMPORTED', 'STATUS_IMPORT_OK', 'STATUS_IMPORT_PROBLEM', 'STATUS_IMPORT_RES', 'STATUS_INV_RECP', 'STATUS_KEYEXPIRED', 'STATUS_KEYREVOKED', 'STATUS_KEY_CREATED', 'STATUS_LEAVE', 'STATUS_MISSING_PASSPHRASE', 'STATUS_NEED_PASSPHRASE', 'STATUS_NEED_PASSPHRASE_SYM', 'STATUS_NEWSIG', 'STATUS_NODATA', 'STATUS_NOTATION_DATA', 'STATUS_NOTATION_NAME', 'STATUS_NO_PUBKEY', 'STATUS_NO_RECP', 'STATUS_NO_SECKEY', 'STATUS_POLICY_URL', 'STATUS_PROGRESS', 'STATUS_REVKEYSIG', 'STATUS_RSA_OR_IDEA', 'STATUS_SESSION_KEY', 'STATUS_SHM_GET', 'STATUS_SHM_GET_BOOL', 'STATUS_SHM_GET_HIDDEN', 'STATUS_SHM_INFO', 'STATUS_SIGEXPIRED', 'STATUS_SIG_CREATED', 'STATUS_SIG_ID', 'STATUS_TRUNCATED', 'STATUS_TRUST_FULLY', 'STATUS_TRUST_MARGINAL', 'STATUS_TRUST_NEVER', 'STATUS_TRUST_ULTIMATE', 'STATUS_TRUST_UNDEFINED', 'STATUS_UNEXPECTED', 'STATUS_USERID_HINT', 'STATUS_VALIDSIG', 'Signature', 'Subkey', 'UserId', 'VALIDITY_FULL', 'VALIDITY_MARGINAL', 'VALIDITY_NEVER', 'VALIDITY_ULTIMATE', 'VALIDITY_UNDEFINED', 'VALIDITY_UNKNOWN', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', '_gpgme', 'gpgme_version']

>> dir(gpgme.Context)
['__class__', '__delattr__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'armor', 'card_edit', 'decrypt', 'decrypt_verify', 'delete', 'edit', 'encrypt', 'encrypt_sign', 'export', 'genkey', 'get_key', 'import_', 'include_certs', 'keylist', 'keylist_mode', 'passphrase_cb', 'progress_cb', 'protocol', 'set_engine_info', 'set_locale', 'sign', 'signers', 'textmode', 'verify']

>>> dir(gpgme.Context().encrypt)
['__call__', '__class__', '__cmp__', '__delattr__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__self__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']

>>> dir(gpgme.Context().decrypt)
['__call__', '__class__', '__cmp__', '__delattr__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__self__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']

```

If you don't know how to do this with pygpgme, but you know another method, that would be great, so long as it's not just invoking the non-Python gpg program to do its stuff.

---

### Post by kumoshk on 2014-03-02
[http://pythonhosted.org/pyskein/threefish.html](http://pythonhosted.org/pyskein/threefish.html)

The above link may address my needs. Ack. I guess that's for Python 3. I'm using 2.x. I may be able to figure out the pygpgme way soon.

---

### Post by kumoshk on 2014-03-03
I found the following link (initiallly from another website that didn't give the source code, but I contacted the owner and got this URL):
[https://bitbucket.org/brendanlong/python-encryption](https://bitbucket.org/brendanlong/python-encryption)

You can also get it from
git clone [https://bitbucket.org/brendanlong/python-encryption.git](https://bitbucket.org/brendanlong/python-encryption.git)

Anyway, this allows me to encrypt or password-protect files in my program how I want. I don't know how secure it is, but whoever made it seems to be knowledgable. I made the code work on Python 2.7 simply by changing a couple print statements that were incompatible. The code was initially made for Python 3. I think it runs faster in Python 3 for some reason, though. Maybe I'll port my code.

Anyway, it's public domain code, which is very nice (as is PyCrypto, which it uses). So, I can take out what I want, make my methods from it and such. Thank you very much, everyone involved in making that. I do like the idea of using multiple encryption methods, though. That way, even if someone spends ages figuring out how to crack AES or whatever, they'll still have to figure out the next method.

I'm still planning to figure out the gpg method one of these days. It's probably easier than I'm thinking.

If you're curious to know what I'm making, it's a hypertext fiction authoring environment. The encryption is to password-protect portions of the text (or the whole thing). This is useful for journals and things where you want some stuff to be readable to anyone who has access to the files, and other stuff private. It's useful for other stuff, too, like preventing people from just looking at the files or source code to figure out how to beat a game (given it's not an Internet game where the server keeps all the secrets). For instance, if there's a secret word you need to figure out to unlock something.

100000 iterations is kind of slow on my computer, though, and probably overkill for my purposes. Fortunately, I think I can get away with less until everyone gets faster computers.

This should be helpful for anyone looking to password-protect files in Python.

I don't know that this compresses your files like gpg would, though.

---

### Post by kumoshk on 2014-05-07
Okay, so far, I've figured out this, for pygpgme:

gpgme.Context.encrypt(gpgme.Context(), None, ?, ?, ?)

The first parameter is a Context object. The second needs to be None, if you want symmetric encryption. I have no idea what the last three are, but faking some, I got a prompt for a password to pop up, interestingly (although I still got an error).

Here are some notes of things I've talked about already, with links I didn't mention:

"gpgme_op_encrypt supports symmetric encryption by passing NULL as the recipient
list. ctx.encrypt() in pygpgme cannot currently perform that operation."

[https://bugs.launchpad.net/pygpgme/+bug/295918](https://bugs.launchpad.net/pygpgme/+bug/295918)


See the release notes on this URL:
[https://launchpad.net/pygpgme/+milestone/0.2](https://launchpad.net/pygpgme/+milestone/0.2) ("* Add support for symmetric encryption in encrypt().")

---

