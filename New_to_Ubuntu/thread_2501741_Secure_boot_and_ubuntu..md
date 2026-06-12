---
title: "Secure boot and ubuntu."
date: 2024-10-19
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-19
Heyo guys,

In setting > Privacy and Security > Device security it says that:

TMP v2.0 is with a green tick at 2024 - 10 - 19 14:21:42
TMP v2.0 is with a red x at 2024 - 10 - 17 11:42:02
Linux Kernal Verification red x 2024 - 10 - 17 10:01:53
Linux Kernal Verification green tick 2024 - 10 - 16 20:31:48

Also says that Secure boot is off.  I thought that linux couldn't run with secure boot so I turned it off.

The tpm stuff should be still on cause I left that on when in bios on my i7-8700 CPU.

---

### Post by tea for one on 2024-10-19
> **shadowtabby said:**
> I thought that linux couldn't run with secure boot so I turned it off
Secure boot enabled/disabled should not prevent Ubuntu booting.
Other Linux distributions may have different configurations.

TPM enabled (and its various iterations) can prevent Linux distributions from booting

---

### Post by shadowtabby on 2024-10-19
Heyo,

Thank you for your reply.

So in your reason for edit, you say TPM >TPM Enabled.  Are you telling me my TPM is still enabled?

Also should I turn on secure boot?  IDK if I should or not.  I had it on when I was using win 11pro.

---

### Post by tea for one on 2024-10-19
> **shadowtabby said:**
> So in your reason for edit, you say TPM >TPM Enabled.  Are you telling me my TPM is still enabled?
I changed the text to clarify that some PCs do not allow Linux distros to boot with TPM enabled.
I have a cheap 'n' cheerful Lenovo netbook where TPM must be disabled to boot Xubuntu.
I've no idea if you have TPM enabled - it's really your choice.
> **shadowtabby said:**
> Also should I turn on secure boot?  IDK if I should or not.  I had it on when I was using win 11pro.
Again, your choice.
Personally, I always disable TPM and Secure Boot.
These security features offer little benefit for home users.
It's a different situation for enterprise/commercial operations where the management need more security.

---

### Post by shadowtabby on 2024-10-19
Heyo.

Okies thank you muchly.

---

