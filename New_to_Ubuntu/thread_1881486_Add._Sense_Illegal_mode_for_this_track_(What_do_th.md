---
title: "Add. Sense: Illegal mode for this track (What do these log messages mean:)"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by ufuser01 on 2011-11-15
I iinstalled Ubuntu and see these messages in the log. What do these messages mean? I don't see any downside to the PC's functionality (yet) despite these messages.

Thanks. 

```
[   25.822452] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.822456] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   25.822461] Info fld=0xa727
[   25.822462] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   25.822468] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   25.822477] end_request: I/O error, dev sr0, sector 171160
[   25.822480] Buffer I/O error on device sr0, logical block 21395
[   25.997212] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.997215] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   25.997218] Info fld=0xa727
[   25.997220] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   25.997224] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   25.997232] end_request: I/O error, dev sr0, sector 171160
[   25.997235] Buffer I/O error on device sr0, logical block 21395
[   26.156126] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.156130] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   26.156133] Info fld=0xa727
[   26.156135] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   26.156139] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   26.156147] end_request: I/O error, dev sr0, sector 171160
[   26.156149] Buffer I/O error on device sr0, logical block 21395
[   26.329703] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.329707] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   26.329710] Info fld=0xa727
[   26.329712] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   26.329716] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   26.329725] end_request: I/O error, dev sr0, sector 171160
[   26.329728] Buffer I/O error on device sr0, logical block 21395
[   26.504295] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.504299] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   26.504303] Info fld=0xa727
[   26.504304] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   26.504310] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   26.504319] end_request: I/O error, dev sr0, sector 171160
[   26.504322] Buffer I/O error on device sr0, logical block 21395
[   26.678455] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.678459] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   26.678462] Info fld=0xa727
[   26.678463] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   26.678467] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   26.678476] end_request: I/O error, dev sr0, sector 171160
[   26.678478] Buffer I/O error on device sr0, logical block 21395
[   26.804480] eth0_rename: no IPv6 routers present
[   26.852648] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   26.852651] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   26.852655] Info fld=0xa727
[   26.852656] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   26.852660] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   26.852669] end_request: I/O error, dev sr0, sector 171160
[   26.852671] Buffer I/O error on device sr0, logical block 21395
[   27.131400] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.131403] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   27.131406] Info fld=0xa727
[   27.131408] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   27.131412] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   27.131420] end_request: I/O error, dev sr0, sector 171160
[   27.131422] Buffer I/O error on device sr0, logical block 21395
[   27.305544] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.305547] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   27.305550] Info fld=0xa727
[   27.305552] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   27.305556] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   27.305564] end_request: I/O error, dev sr0, sector 171160
[   27.305566] Buffer I/O error on device sr0, logical block 21395
[   27.479719] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.479722] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   27.479726] Info fld=0xa727
[   27.479727] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   27.479731] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   27.479740] end_request: I/O error, dev sr0, sector 171160
[   27.479742] Buffer I/O error on device sr0, logical block 21395
[   28.681543] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.681547] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   28.681551] Info fld=0xa727
[   28.681552] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   28.681557] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   28.681565] end_request: I/O error, dev sr0, sector 171160
[   28.855764] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.855768] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   28.855772] Info fld=0xa727
[   28.855773] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   28.855777] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   28.855786] end_request: I/O error, dev sr0, sector 171160
[   29.029958] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.029961] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.029964] Info fld=0xa727
[   29.029966] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.029970] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.029978] end_request: I/O error, dev sr0, sector 171160
[   29.203997] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.204000] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.204003] Info fld=0xa727
[   29.204005] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.204009] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.204017] end_request: I/O error, dev sr0, sector 171160
[   29.378241] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.378245] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.378249] Info fld=0xa727
[   29.378251] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.378255] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.378264] end_request: I/O error, dev sr0, sector 171160
[   29.552416] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.552420] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.552423] Info fld=0xa727
[   29.552425] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.552429] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.552437] end_request: I/O error, dev sr0, sector 171160
[   29.726653] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.726657] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.726660] Info fld=0xa727
[   29.726662] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.726666] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.726674] end_request: I/O error, dev sr0, sector 171160
[   29.900766] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.900770] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   29.900774] Info fld=0xa727
[   29.900776] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   29.900780] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   29.900789] end_request: I/O error, dev sr0, sector 171160
[   30.074943] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.074947] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   30.074951] Info fld=0xa727
[   30.074952] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   30.074957] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 a7 26 00 00 02 00
[   30.074966] end_request: I/O error, dev sr0, sector 171160
[   35.433759] ISO 9660 Extensions: Microsoft Joliet Level 3
[   35.456661] ISO 9660 Extensions: RRIP_1991A
```

---

### Post by Daveth on 2011-11-15
can you tell us what you installed it on, and how please?

---

### Post by oldos2er on 2011-11-15
"sr0" is your CD or DVD drive. Also "Microsoft Joliet Level 3" refers to CDFS used by optical drives. Was there a disc in the drive when you booted?

---

### Post by ufuser01 on 2011-11-15
Thanks.

It was a data disk (no OS). But what do those messages mean?

> **oldos2er said:**
> "sr0" is your CD or DVD drive. Also "Microsoft Joliet Level 3" refers to CDFS used by optical drives. Was there a disc in the drive when you booted?

---

### Post by Daveth on 2011-11-18
that your error report was centred on that device, so a cd drive issue

---

