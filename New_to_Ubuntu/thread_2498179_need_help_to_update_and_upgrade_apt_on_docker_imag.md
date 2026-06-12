---
title: "need help to update and upgrade apt on docker image"
date: 2024-06-03
forum: New to Ubuntu
---

### Post by spicca on 2024-06-03
hello! I am using ubuntu 22.04 on docker image and I need help to update and upgrading apt.

first, I make a new docker image using docker run command below:
docker run -itd --name "mydockerimage" -p (ports) ubuntu:22.04

and I connect to my docker image using this command:
docker exec -it mydockerimage /bin/bash

finally I try to update & upgrade apt by this command, but the error occurs.
apt update && apt upgrade -y

the error is:
```
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [129 kB]
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease [128 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [2129 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [1377 kB]
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:1376564 [weak]
   - SHA256:8e7faf4c8cf9db962404f4ce2698593375e8b9d22663710fdc19625454efb271
   - SHA1:caa116103769c0c028a1a1831f41d43ae2af9a0e [weak]
   - MD5Sum:be240b0f10c9a82515cb512c24137289 [weak]
  Hashes of received file:
   - SHA256:df6ef71c39b787e1cd4b8ec118787fdccf66f4447a4d6fc10dcccaab7a8172da
   - SHA1:b2df9678714ae277eeae7747c541030a2f0dac78 [weak]
   - MD5Sum:7fd0108d0d8a5a779d6be517b5801582 [weak]
   - Filesize:1376564 [weak]
  Last modification reported: Mon, 03 Jun 2024 01:16:15 +0000
  Release file created at: Mon, 03 Jun 2024 03:23:37 +0000
Fetched 1634 kB in 3s (576 kB/s)
Reading package lists... Done
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/binary-amd64/by-hash/SHA256/8e7faf4c8cf9db962404f4ce2698593375e8b9d22663710fdc19625454efb271](http://archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/binary-amd64/by-hash/SHA256/8e7faf4c8cf9db962404f4ce2698593375e8b9d22663710fdc19625454efb271)  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:1376564 [weak]
    - SHA256:8e7faf4c8cf9db962404f4ce2698593375e8b9d22663710fdc19625454efb271
    - SHA1:caa116103769c0c028a1a1831f41d43ae2af9a0e [weak]
    - MD5Sum:be240b0f10c9a82515cb512c24137289 [weak]
   Hashes of received file:
    - SHA256:df6ef71c39b787e1cd4b8ec118787fdccf66f4447a4d6fc10dcccaab7a8172da
    - SHA1:b2df9678714ae277eeae7747c541030a2f0dac78 [weak]
    - MD5Sum:7fd0108d0d8a5a779d6be517b5801582 [weak]
    - Filesize:1376564 [weak]
   Last modification reported: Mon, 03 Jun 2024 01:16:15 +0000
   Release file created at: Mon, 03 Jun 2024 03:23:37 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.

```
please help me if anything I can try to solve this problem. thank you.

---

### Post by ActionParsnip on 2024-06-03
Is Ubuntu in WSL by any chance? If so then you may need this:
[https://askubuntu.com/questions/1235914/hash-sum-mismatch-error-due-to-identical-sha1-and-md5-but-different-sha256](https://askubuntu.com/questions/1235914/hash-sum-mismatch-error-due-to-identical-sha1-and-md5-but-different-sha256)

---

### Post by spicca on 2024-06-06
for some reason I don't know, apt update and apt upgrade is work fine.

---

