---
title: "year not found in bootlog  log file"
date: 2024-04-05
forum: New to Ubuntu
---

### Post by atik-mahedvi on 2024-04-05
Dear Team,

We have installed 22.04 LTS, We did not find the year  in boot log file. when type journalctl -b command. i am getting below output. my requirement is year is print in this logs?  

kindly suugest?

root@SP3SIGNZYAPP17PROD:~# journalctl -b
Mar 26 10:48:07 SP3SIGNZYAPP17PROD sudo[496532]: pam_unix(sudo-i:session): session closed for user root
Mar 29 02:02:01 SP3SIGNZYAPP17PROD CRON[2205138]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 10)
Mar 29 02:02:01 SP3SIGNZYAPP17PROD CRON[2205137]: pam_unix(cron:session): session closed for user root
Mar 29 02:02:02 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-b8759003bb22a16f7a2b873b86bb78c48d7da3e8c52ccff8eb88dca1516657f2-runc.6UFPLu.mount: Deactivated successfully.
Mar 29 02:02:02 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8bf9859ce39d0b5353b78d3e73c7e7fe1199f3473513998c73cfde19350306be-runc.uYQB1Q.mount: Deactivated successfully.
Mar 29 02:02:03 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8fbc4c422377f82c194e1aeb6e03c3f0f384f1123b92b8fc528b360e13b2d7b3-runc.5Rtf5e.mount: Deactivated successfully.
Mar 29 02:02:32 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-b8759003bb22a16f7a2b873b86bb78c48d7da3e8c52ccff8eb88dca1516657f2-runc.xaP2av.mount: Deactivated successfully.
Mar 29 02:02:32 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8bf9859ce39d0b5353b78d3e73c7e7fe1199f3473513998c73cfde19350306be-runc.rH95PR.mount: Deactivated successfully.
Mar 29 02:02:33 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8fbc4c422377f82c194e1aeb6e03c3f0f384f1123b92b8fc528b360e13b2d7b3-runc.uvnRjg.mount: Deactivated successfully.
Mar 29 02:03:02 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-b8759003bb22a16f7a2b873b86bb78c48d7da3e8c52ccff8eb88dca1516657f2-runc.AE3YpR.mount: Deactivated successfully.
Mar 29 02:03:02 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8bf9859ce39d0b5353b78d3e73c7e7fe1199f3473513998c73cfde19350306be-runc.WAMpgo.mount: Deactivated successfully.
Mar 29 02:03:32 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-b8759003bb22a16f7a2b873b86bb78c48d7da3e8c52ccff8eb88dca1516657f2-runc.IfBr7c.mount: Deactivated successfully.
Mar 29 02:03:32 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8bf9859ce39d0b5353b78d3e73c7e7fe1199f3473513998c73cfde19350306be-runc.aJSOg6.mount: Deactivated successfully.
Mar 29 02:03:33 SP3SIGNZYAPP17PROD systemd[1]: run-docker-runtime\x2drunc-moby-8fbc4c422377f82c194e1aeb6e03c3f0f384f1123b92b8fc528b360e13b2d7b3-runc.PZKtWo.mount: Deactivated successfully.

---

