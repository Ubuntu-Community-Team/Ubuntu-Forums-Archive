---
title: "Problems downloading from SFTP using Paramiko"
date: 2011-02-25
forum: Programming Talk
---

### Post by 102jon on 2011-02-25
Hi, I am writing an application that downloads files from an SFTP server to a local directory. So far I've got the connection working but I am getting an IOError when I try to download. It is errno 13: Permission denied to local path. Here is my code:

```
SFTP_OBP_PATH = "/home/cust_ee_internal/spacequest_receiver"
SFTP_SPECTRUM_PATH = "/home/cust_ee_internal/spectrum_processor"
GLOBAL_OBP_DIR = "D:\\Users\\jonathan.martin\\Desktop\\CSA Data\\global\\obp\\gnm"

#Connect to SFTP
update_check = sftp_communication.SFTPSimpleClient(SFTP_HOST_TUPLE_GET, SFTP_USER_GET, password)
fileList = update_check.list_in(SFTP_OBP_PATH)
getTime = update_check.modified_times(fileList, SFTP_OBP_PATH)

#Download and upload all updated OBP files
for i in range(len(fileList)):
    if int(str(getTime[i])[5:7]) <= 12 and int(str(getTime[i])[5:7]) > 2:
        update_check.download_from_sftp_server(SFTP_OBP_PATH + '/' + fileList[i], GLOBAL_OBP_DIR, SFTP_OBP_PATH)
```

Help would be greatly appreciated.

---

