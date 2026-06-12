---
title: "How to set public key for Ubuntu 22.04?"
date: 2023-03-28
forum: New to Ubuntu
---

### Post by haivcci on 2023-03-28
Hi
I have a VPS is running Ubuntu 22.04

I usually use Puttygen to general the public key then paste to ~/.ssh/authorized_keys, then use the private key to login to the VPS on my Windows via Putty.

But yesterday, I can't make it working on Ubuntu 22.04. Seem this version does not support the old way I did.

Could you please tell me how to do? I do search on Google and still not find the correct way to make it works.

Thanks

---

### Post by ActionParsnip on 2023-03-28
if you SSH using Powershell, you can useL
```

ssh -vvvvvvv -i c:\path\to\privatekey.ppk username@server

```
The output should be useful in troubleshooting

---

### Post by MAFoElffen on 2023-03-29
Windows 10 or 11...

Open a Powershell Prompt window...
```

ssh-keygen
scp $env:USERPROFILE\.ssh\id_rsa.pub user_name@server_ip:~/.ssh/windows_rsa.pub
ssh username@server_ip

```
Log in, say yes. Enter credentials.

Check a few things first
```

ls -l ~/.ssh/

```
Check to see if that file authorized_keys exists. That it is permissions 600. Check to see if windows_rsa.pub exists.

If the authorized_keys file does not exist yet, then do these two steps
```

touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

```
Then add your key to that file
```

cat ~/.ssh/windows_rsa.pub >> authorized_keys

```
Then exit out and ssh back to it, to test if it respects the auth key.

---

### Post by haivcci on 2023-03-29
I found the problem. RSA is not support anymore in Ubuntu 22.04 (openssh new version I think). Instead of RSA, I created the public key using option ECDSA and it works.

Thank you everyone for support.

---

### Post by mIk3_08 on 2023-03-29
> **haivcci said:**
> I found the problem. RSA is not support anymore in Ubuntu 22.04 (openssh new version I think). Instead of RSA, I created the public key using option ECDSA and it works.
Thank you everyone for support.

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by ActionParsnip on 2023-03-29
Mentally noted. I've always used ECDSA myself.

---

### Post by MAFoElffen on 2023-03-29
Glad that things worked for you...
> **haivcci said:**
> I found the problem. [COLOR=#ff0000]RSA is not support anymore in Ubuntu 22.04 (openssh new version I think).[/COLOR] Instead of RSA, I created the public key using option ECDSA and it works.
??? 

"Who" says? OpenSSH 9.3 still supports RSA.

From the OpenSSH Release Notes for 9.3/9.3p1 (2023-03-15), that refers to their current man ssh-keygen
> 
 -t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa
    Specifies the type of key to create. The possible values are &#8220;dsa&#8221;, &#8220;ecdsa&#8221;, &#8220;ecdsa-sk&#8221;, &#8220;ed25519&#8221;, &#8220;ed25519-sk&#8221;, or &#8220;rsa&#8221;.

    This flag may also be used to specify the desired signature type when signing certificates using an RSA CA key. The available RSA signature variants are &#8220;ssh-rsa&#8221; (SHA1 signatures, not recommended), &#8220;rsa-sha2-256&#8221;, and &#8220;rsa-sha2-512&#8221; (the default).

 If you do not add the -t option, RSA (rsa-sha2-512) is the default...
```

openssh-server/jammy-updates,now 1:8.9p1-3ubuntu0.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.2 LTS
mafoelffen@Mikes-ThinkPad-T520:~$ apt list openssh-server --installed
Listing... Done
openssh-server/jammy-updates,now 1:8.9p1-3ubuntu0.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```

---

