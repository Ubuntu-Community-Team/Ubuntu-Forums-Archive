---
title: "Installing Electrum, &quot;TypeError: Descriptors cannot not be created directly.&quot;"
date: 2022-07-14
forum: New to Ubuntu
---

### Post by norahlo on 2022-07-14
Installed as per the instructions on Electrum.org. Or tried to, anyway. Did I do something wrong? (Ubuntu 20.04; Beginner)

```
$ electrum
Traceback (most recent call last):
  File "/home/user/.local/bin/electrum", line 87, in <module>
    from electrum.logging import get_logger, configure_logging # import logging submodule first
  File "/home/user/.local/lib/python3.8/site-packages/electrum/__init__.py", line 16, in <module>
    from wallet import Wallet
  File "/home/user/.local/lib/python3.8/site-packages/electrum/wallet.py", line 68, in <module>
    from .storage import StorageEncryptionVersion, WalletStorage
  File "/home/user/.local/lib/python3.8/site-packages/electrum/storage.py", line 37, in <module>
    from .wallet_db import WalletDB
  File "/home/user/.local/lib/python3.8/site-packages/electrum/wallet_db.py", line 45, in <module>
    from .paymentrequest import PaymentRequest
  File "/home/user/.local/lib/python3.8/site-packages/electrum/paymentrequest.py", line 37, in <module>
    from . import paymentrequest_pb2 as pb2
  File "/home/user/.local/lib/python3.8/site-packages/electrum/paymentrequest_pb2.py", line 36, in <module>
    _descriptor.FieldDescriptor(
  File "/home/user/.local/lib/python3.8/site-packages/google/protobuf/descriptor.py", line 560, in __new__
    _message.Message._CheckCalledFromGeneratedFile()
TypeError: Descriptors cannot not be created directly.
If this call came from a _pb2.py file, your generated code is out of date and must be regenerated with protoc >= 3.19.0.
If you cannot immediately regenerate you protos, some other possible workarounds are:
 1. Downgrade the protobuf package to 3.20.x or lower.
 2. Set PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python (but this will use pure-Python parsing and will be much slower).

More information: https://developers.google.com/protocol-buffers/docs/news/2022-05-06#python-updates
```

---

### Post by norahlo on 2022-07-20
Reinstalled via python sources a couple times as I had done. No issues during the installation commands and am able to run without installing. The problem is '[FONT=courier new]electrum[/FONT]'. Looked into it but still don't know what's going on. If you have an idea what the issue might've been, a solution, or could explain the error to me, it would still be appreciated.

Marking this as solved because I had success with the appimage. 

In case anyone comes to this thread in the future looking for help with the same or a similar issue, these are the commands I used:
```

wget https://raw.githubusercontent.com/spesmilo/electrum/master/pubkeys/ThomasV.asc
gpg --import ThomasV.asc
wget https://download.electrum.org/4.2.2/electrum-4.2.2-x86_64.AppImage
wget https://download.electrum.org/4.2.2/electrum-4.2.2-x86_64.AppImage.asc
chmod +x electrum-4.2.2-x86_64.AppImage
gpg --verify electrum-4.2.2-x86_64.AppImage.asc

```

And then to open:
```
./electrum-4.2.2-x86_64.AppImage
```

---

