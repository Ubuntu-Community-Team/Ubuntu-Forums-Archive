---
title: "Generate Detatched/Signature File"
date: 2014-04-27
forum: Programming Talk
---

### Post by nos-developer on 2014-04-27
I am creating a few metalinks for an installer similar to  wubi. It requires me to create a MD5SUMS-metalink file which I have done  but the program will not continue because it requires a *MD5SUMS-metalink.gpg* file.

  I am not sure how to generate this and it needs to be something along the lines of
  
```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.11 (GNU/Linux)

iEYEABECAAYFAlNRiYIACgkQRhgUM/u3VFGPaACcC1l9IwsQdOzI7kJbgQTm1jEw
RloAnRwAtqUAlc+p5/EKpyIsA6JL4GDi
=IMv7
-----END PGP SIGNATURE-----

```

 which is what the official Ubuntu one contains.

  How can I generate this detached signature in Ubuntu?

PS I am not sure if this is where I should post this but I couldn't find a better category.

---

