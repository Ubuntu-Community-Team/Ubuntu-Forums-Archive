---
title: "Ubuntu 12.04 all USB stopped working"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Sagitta12 on 2012-10-16
First I thought it was the wireless USB mouse, but then I discovered nothing worked on any of the 4 USB ports, no USB stick, camera, no mouse.
Read many threads and tried many solutions, nothing seems to help. Been mucking around with this for two days now....
Where to start to get this fixed????

---

### Post by cortman on 2012-10-16
Can you try reloading the kernel module?

```
modprobe ehci-hcd
```

---

### Post by Sagitta12 on 2012-10-16
Just tried that - no luck..
That is - copying it in a terminal window, nothing happened..

---

### Post by NikTh on 2012-10-16
Hi , 

we must clarify if this is a hardware of software problem.  Ubuntu (Linux) has very helpful logs that can be used for debugging  problems.

Lets see some log files.
Open a terminal and do 

```
dmesg >> dmesg.txt
cat /var/log/kern.log.1 >> kern-old.txt
cat /var/log/Xorg.0.log >> Xorg.txt
```3  files with names dmesg.txt kern-old.txt and xorg.txt will be created inside  your /home directory. Attach the files here by click on "New Reply" and  click on paperclip symbol in message toolbar.

Give some time so people who knows will examine your logs. 

Thanks

---

### Post by Sagitta12 on 2012-10-16
```

numerate USB device on port 2
[ 5695.940266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5697.388296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5699.436070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5699.988348] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5702.036263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5703.132289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5705.180259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5706.276291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5708.356133] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5709.260182] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5711.308078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5711.892247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5713.940087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5715.900298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5717.948261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5718.424273] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5718.812291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5720.860262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5721.668299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5723.716260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5723.956064] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5724.280288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5726.328098] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5727.232306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5729.280255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5731.016297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5733.064237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5734.000279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5736.048270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5736.352260] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5736.688295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5738.736161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5739.608091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5741.784204] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5742.656283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5744.704196] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5745.768091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5747.880261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5748.688281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5750.736267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5751.352287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5753.464261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5754.176301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5756.224119] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5756.528065] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5757.108302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5759.156269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5760.380301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5762.428089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5763.172301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5765.224260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5766.832297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5768.880169] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5769.528186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5771.576181] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5772.320225] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5774.368269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5775.528127] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5777.608259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5778.544293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5780.592255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5780.992061] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5781.316289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5783.364254] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5784.716298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5786.764085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5788.052086] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5790.100261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5790.908272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5793.084071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5794.180287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5796.228260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5796.532275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5798.328120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5800.376071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5800.680149] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5801.420181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5803.468190] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5804.340243] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5806.388268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5807.644297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5810.012096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5810.564241] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5812.612217] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5813.900293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5815.948258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5816.692116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5818.744235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5819.904281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5821.956072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5822.988119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5825.072272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5825.472275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5825.956286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5828.004242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5828.652293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5830.700070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5831.508161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5833.748196] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5834.428230] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5836.476059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5837.700298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5839.780262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5841.616088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5843.664278] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5844.128284] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5844.676078] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5846.724041] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5847.820101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5849.932261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5850.652274] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5851.168301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5853.280261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5853.680254] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5854.004298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5856.056083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5857.056302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5859.360249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5859.664269] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5859.988311] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5862.036129] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5863.420099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5865.472222] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5866.056272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5868.104258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5869.168288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5871.216273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5871.744102] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5872.644286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5874.700067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5875.924138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5877.980255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5878.696101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5880.744058] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5881.592087] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5881.928235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5883.976270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5884.560254] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5886.928255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5887.456257] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5887.844267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5889.892241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5891.436260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5893.516140] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5893.788167] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5894.496202] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5896.768244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5897.008275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5898.292269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5900.344259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5901.024256] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5901.756294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5903.900262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5904.676269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5906.788247] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5907.500268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5909.548253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5910.196296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5912.244262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5913.756293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5915.804267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5916.484290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5918.532269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5919.188271] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5919.512249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5921.816108] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5925.448069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5927.928201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5930.248053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5933.212087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5934.488227] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5936.548243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5939.092057] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5941.576107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5944.344267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5944.680275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5946.868251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5947.176082] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5949.620087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5951.908220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5953.036291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5955.564145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5956.308208] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5958.964257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5959.964288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5962.556260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5963.588292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5965.860270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5966.828283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5969.004091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5969.588080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5971.764255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5972.604268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5974.940270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5975.556264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5978.180266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5978.892237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5981.132268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5981.940250] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5984.404153] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5985.116203] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5987.292178] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5988.164241] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5990.568168] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5991.344295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5993.520260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5994.136204] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5996.540257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 5997.092291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 5999.396254] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6000.652280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6002.828261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6003.636266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6005.972257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6006.620134] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6008.796055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6009.796302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6012.200267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6013.264302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6015.440158] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6016.280180] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6018.328188] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6019.072247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6021.344261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6021.896247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6024.072080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6024.768300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6027.008061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6027.976115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6030.024070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6030.576291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6032.624145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6033.352294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6035.532258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6036.212106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6038.260067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6038.812264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6041.148270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6041.908289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6044.084122] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6044.860292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6047.036096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6047.876186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6050.052046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6050.396268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6052.444252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6053.828300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6055.876264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6056.940293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6059.116252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6059.620301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6061.796184] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6062.428124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6064.604223] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6065.156112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6067.204265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6067.868299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6070.048235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6070.392281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6072.568272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6073.136114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6075.188103] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6075.564108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6077.740129] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6078.292170] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6080.340205] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6080.716269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6082.764262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6083.604287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6085.652252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6086.492293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6088.668259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6088.980276] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6091.028255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6091.564285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6093.612264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6093.956299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6095.876095] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6096.348269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6098.268294] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6099.220287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6101.276255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6102.020298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6103.940255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6104.348295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6106.400268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6107.032291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6109.080149] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6109.456149] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6111.504205] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6112.184263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6114.232268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6115.152295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6117.072255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6117.384287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6119.304251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6119.936298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6121.856268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6122.456208] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6124.376259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6124.688300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6126.612232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6128.660249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6129.260288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6131.180251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6131.620285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6133.540267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6133.980299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6135.900234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6136.500269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6138.420135] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6139.052095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6140.972183] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6141.348129] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6143.268229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6143.996094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6145.916263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6146.228108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6148.148083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6148.748291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6150.668263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6151.748307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6153.668269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6154.012288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6155.932259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6156.724295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6158.644094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6159.084285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6161.004300] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6161.316299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6163.236275] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6163.548287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6165.468229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6165.780273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6167.956054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6168.940085] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6170.860147] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6171.396157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6173.316104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6174.076073] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6175.996078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6176.308291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6178.228270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6178.860117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6180.780267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6181.252297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6183.172260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6183.612283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6185.532253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6185.972080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6187.900073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6188.564300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6190.484092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6190.796293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6192.716267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6193.028297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6194.948235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6195.456236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6197.632261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6197.944283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6199.864062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6200.240177] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6202.160072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6202.568145] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6204.488237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6204.864132] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6206.788050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6207.164306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6209.084274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6209.624155] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6211.544255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6212.240185] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6214.160240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6214.824100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6216.744271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6217.568076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6219.492275] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6220.320236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6222.240088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6222.648287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6224.572066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6226.496074] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 6226.680082] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6228.600272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6228.912244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6230.832151] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6231.144128] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6233.064075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6233.376217] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6235.296250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6235.768277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6237.688213] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6238.032109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6239.952093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6240.264117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6242.188289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6244.108232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6244.420293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6246.344065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6246.688285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6248.608101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6249.336257] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6251.264225] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6251.832107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6253.752261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6254.192117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6256.116251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6256.620275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6258.540259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6258.916268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6260.836068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6261.148118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6263.068120] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6263.380163] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6265.300190] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6265.612257] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6267.532305] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6267.876245] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6269.796258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6270.208217] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6272.128234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6272.760248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6274.680260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6275.568295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6277.488242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6277.896289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6279.816061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6280.192120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6282.112086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6282.552263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6284.472259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6284.944287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6286.868078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6287.372091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6289.292086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6290.408089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6292.328139] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6292.864162] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6294.784073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6296.088115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6298.008256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6298.672100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6300.848054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6301.256268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6303.176273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6304.016101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6305.936269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6306.280094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6308.200276] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6309.696280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6311.616266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6312.280270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6314.328269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6314.992091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6316.912259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6317.544287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6319.464241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6319.936088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6322.112116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6323.384200] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6325.432170] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6325.904197] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6327.824243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6328.136252] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6330.064247] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6330.408291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6332.328240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6332.800291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6334.976272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6336.632155] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6338.808263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6339.120219] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6341.040270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6341.544282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6343.592297] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6343.904285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6346.080073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6346.552202] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6348.476052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6349.236291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6351.156218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6351.788096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6353.932092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6354.660169] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6356.580115] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6357.884180] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6359.932083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6360.500296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6362.420258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6363.468271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6365.644245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6365.956306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6367.876271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6369.924049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6370.332112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6372.380218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6372.884076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6374.932258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6375.244294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6377.292227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6377.732291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6379.908259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6380.380116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6382.620268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6383.524291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6385.700090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6386.444178] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6388.620186] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6389.812084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6392.116059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6392.716289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6394.892260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6395.332117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6397.508209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6397.980292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6400.124274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6400.868270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6403.044220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6403.660295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6405.712238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6406.776295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6408.824259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6409.728267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6411.776094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6412.648100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6414.824053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6416.048142] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6418.096166] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6419.384248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6421.560145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6422.112291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6424.352073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6426.392267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6428.568236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6429.376098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6431.552085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6432.104153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6434.152260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6434.800286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6436.976247] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6437.352115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6439.592272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6440.308318] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6442.644269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6443.804285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6445.852068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6446.532186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6448.708176] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6450.868111] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 6451.052161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6453.228100] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6454.036236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6456.220260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6457.108097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6459.444267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6460.124298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6462.588268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6463.780289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6465.828259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6467.404276] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6469.580263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6470.516295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6472.692244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6473.340159] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6475.516256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6476.356286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6478.532138] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6479.276134] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6481.452226] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6482.676283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6484.852262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6485.468071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6487.644270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6488.580089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6491.080075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6491.856289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6494.032256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6495.864290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6498.168112] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6498.912299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6501.120092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6502.152272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6504.552261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6505.200297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6507.568161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6508.216183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6510.652191] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6511.652249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6513.956263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6514.828277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6517.132248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6517.684284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6519.860272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6520.908296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6523.116249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6524.340096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6526.548238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6527.836301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6530.076274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6530.444273] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 6530.992092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6533.168253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6533.816110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6536.152274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6536.736285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6539.008134] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6539.560142] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6541.736185] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6542.288238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6544.464266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6545.692111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6547.868240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6548.420081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6550.468144] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6551.148306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6553.196212] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6553.700296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6555.748262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6556.492292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6558.540252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6559.380305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6561.432229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6561.744110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6563.856270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6564.168294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6566.216087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6566.768299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6568.944248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6569.608183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6571.788174] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6572.164093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6574.212229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6575.020075] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6577.196067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6577.508299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6579.684050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6580.524078] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6582.704066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6583.016084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6585.196236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6585.732134] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6587.780234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6588.444111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6590.492092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6590.900143] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6593.076249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6593.644292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6595.820051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6596.132270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6598.180066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6598.524107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6600.444147] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6601.428104] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6603.348168] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6603.660119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6605.836275] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6606.388301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6608.436241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6608.748117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6610.796291] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6612.004067] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6613.924066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6615.084273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6617.132192] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6617.476299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6619.524078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6620.108301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6622.156090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6622.628303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6625.028054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6625.756135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6627.932047] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6629.064097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6631.240167] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6632.736190] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6634.784218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6635.692101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6637.868262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6638.420295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6640.600257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6641.040286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6642.964062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6643.276303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6645.452270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6646.580294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6648.756260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6649.500278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6651.676242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6652.020203] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6654.068241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6655.260281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6657.436083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6658.180263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6660.356244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6661.100292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6663.148137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6663.924108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6665.972113] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6666.508106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6668.556055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6669.316287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6671.364270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6671.772285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6673.692082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6674.356222] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6676.404070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6676.812102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6678.988275] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6679.716098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6681.768260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6682.384292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6684.560251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6684.904283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6686.952245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6687.456287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6689.376265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6690.024098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6692.072266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6693.568124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6695.748169] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6696.412254] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6698.460271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6699.012287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6701.060225] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6703.476260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6703.820269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6705.996267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6706.340121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6708.260258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6709.196288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6711.372256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6712.052320] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6714.232081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6714.944288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6717.120276] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6719.040066] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 6719.224292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6721.752242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6722.880289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6724.928146] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6725.368187] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6727.544234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6728.960271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6731.136263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6731.720303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6733.960106] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6734.992301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6737.168261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6737.896072] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6739.944164] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6741.744103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6743.792242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6744.600284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6746.780255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6748.228261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6750.280250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6750.896291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6753.072268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6753.416270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6755.468128] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6756.004085] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6758.052221] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6758.364256] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6760.540243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6761.540289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6763.716092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6765.244284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6767.296072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6768.680103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6770.728256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6771.312284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6773.488262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6774.168297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6776.216236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6776.800290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6778.848289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6779.320288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6781.368267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6782.272280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6784.320243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6784.760164] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6786.972159] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6788.260128] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6790.436274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6791.100073] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6793.024203] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6793.432286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6795.616070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6796.344298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6798.264255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6798.576243] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6800.496251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6801.032300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6803.080250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6803.760298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6805.808270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6806.152301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6808.072146] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6808.576291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6810.500240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6810.812275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6812.732230] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6814.780250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6815.284203] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6817.428045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6818.268211] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6820.320239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6820.792283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6822.968263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6823.472290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6825.520065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6826.088282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6828.008271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6828.996292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6831.048086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6831.360286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6833.280219] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6834.104260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6836.024255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6836.960279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6839.008273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6839.544247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6841.468268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6842.132299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6844.056238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6844.560067] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6846.608127] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6847.304125] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6849.224077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6849.776229] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6851.824276] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6852.296280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6854.216262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6854.528238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6856.448239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6858.368243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6858.712297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6860.632256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6862.680269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6863.312264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6865.232064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6865.672283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6867.592082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6867.904292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6869.824259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6871.744117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6872.600294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6874.520268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6874.928103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6876.976167] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6877.352113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6879.404168] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6880.036086] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6882.084254] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6882.844292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6884.892064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6885.268128] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6887.188263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6887.532100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6889.580271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6890.244289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6892.292225] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6893.388111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6895.568269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6896.552318] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6898.472246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6898.784306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6900.708159] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6901.244281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6903.164119] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6903.876111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6905.924264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6906.236289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6908.412161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6908.724199] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6910.644171] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6910.988123] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6912.912082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6913.448090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6915.496046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6915.840116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6917.760137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6919.192296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6921.372276] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6921.908089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6923.828150] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6924.396263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6926.316242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6927.204112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6929.128261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6929.824292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6931.748097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6932.060294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6934.108252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6934.420296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6936.468080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6936.844130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6938.764055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6939.812209] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6942.020199] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6942.396137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6944.316251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6944.628266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6946.552263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6947.472286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6949.392264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6950.572280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6952.492261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6952.964301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6955.012059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6956.220292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6958.140260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6958.452107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6960.372269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6960.716099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6962.892268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6963.204146] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6965.128257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6965.440305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6967.360086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6967.864294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6969.784121] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6970.960125] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6972.880194] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6973.704248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6975.624269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6976.800286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6978.720053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6979.032182] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6980.952266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6981.264282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6983.184255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6983.624288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6985.704076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6986.016101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6987.936259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6988.536300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6990.456252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6991.440280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6993.360268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6994.056289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6995.976264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6996.416294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6998.336255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6998.904077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7000.832169] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7001.656163] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7003.576107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7004.144244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7006.064256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7006.376289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7008.296260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7008.960263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7010.880284] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7011.608294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7013.528259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7014.096292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7016.020081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7016.332167] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7018.252243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7018.724307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7020.644271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7021.116074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7023.036059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7023.892101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7025.816220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7026.288289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7028.208079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7028.840285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7030.760258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7031.072195] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7032.996124] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7033.724188] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7035.644237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7035.956096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7037.876050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7038.444100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7040.364061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7040.804296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7042.724081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7043.836119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7045.756272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7046.068120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7047.988091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7048.300260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7050.224076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7050.568296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7052.488268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7052.800267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7054.724249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7055.036080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7056.956260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7057.492273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7059.412089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7059.852275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7061.772145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7063.076092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7064.996157] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7065.596244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7067.516091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7067.924249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7069.844121] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7071.052269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7072.972067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7073.348268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7075.268100] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7075.612103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7077.532265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7077.844275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7079.764093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7080.076065] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7081.996243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7082.372292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7084.292231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7084.924300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7086.844265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7087.156117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7089.076264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7090.996084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7091.372288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7093.292160] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7094.244169] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7096.164201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7096.988154] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7098.908272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7099.572299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7101.492265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7102.284296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7104.204267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7104.804289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7106.724045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7107.068065] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7108.988101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7109.300097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7111.220073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7111.532278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7113.452243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7113.764298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7115.684063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7116.092285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7118.012045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7118.644126] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7120.568050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7120.912111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7122.832070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7123.304083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7125.224157] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7126.432209] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7128.352087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7128.664114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7130.584248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7131.056121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7132.976248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7133.416113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7135.336052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7136.032277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7137.952238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7138.520100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7140.440066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7140.976290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7142.896265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7143.272090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7145.192260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7145.600291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7147.524061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7148.060101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7149.980256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7150.580095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7152.500260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7152.908304] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7154.828263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7155.524168] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7157.444080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7157.820238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7159.740232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7160.180236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7162.100056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7162.604109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7164.524264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7164.836100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7166.756216] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7167.424124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7169.344116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7170.040267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7171.960042] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7172.272241] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7174.192078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7175.048082] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7176.968074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7177.568263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7179.488054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7179.800084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7181.976190] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7182.544074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7184.464086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7184.904119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7186.824125] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7187.140183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7189.060220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7189.372246] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7191.292046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7191.732085] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7193.652232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7194.124291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7196.044127] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7196.964292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7198.884208] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7199.644295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7201.568240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7201.880291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7203.800265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7204.176103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7206.096233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7207.240109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7209.160274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7209.568264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7211.488262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7212.408249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7214.328238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7214.640295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7216.560086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7217.384173] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7219.432069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7219.840237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7221.760081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7222.264270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7224.184273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7224.496302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7226.424264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7226.928097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7228.848237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7229.160150] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7231.084060] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7231.528275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7233.448256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7234.272071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7236.192214] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7236.824105] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7238.744241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7239.120087] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7241.040052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7241.384081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7243.304137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7245.224249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7245.984259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7247.904053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7248.696165] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7250.616220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7250.992237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7252.912256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7253.704281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7255.628111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7256.100305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7258.020253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7258.332268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7260.252057] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7260.568109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7262.616111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7263.456293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7265.504050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7266.120297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7268.296265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7269.056279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7270.976242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7271.608298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7273.528229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7274.992273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7276.912264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7277.512192] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7279.432156] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7280.000161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7281.920241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7282.264276] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7284.184086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7284.720255] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7286.640256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7287.016299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7288.936289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7289.248310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7291.168265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7291.704294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7293.624089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7293.936268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7295.860262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7296.364302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7298.284092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7298.756286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7300.804257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7301.484125] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7303.532130] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7303.876160] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7305.928083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7306.560119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7308.488098] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7309.152132] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7311.080131] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7312.592153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7314.512127] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7314.888127] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7316.812152] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7317.284166] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7319.368289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7321.184152] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7323.360130] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7324.392162] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7326.316139] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7326.820135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7328.740111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7329.244157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7331.292101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7331.668158] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7333.588092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7334.636157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7336.556102] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7337.652138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7339.708136] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7340.260077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7342.308126] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7343.132113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7345.052243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7345.364298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7347.284239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7348.364294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7350.284269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7350.916289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7352.964069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7353.308303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7355.484242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7355.956115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7357.876183] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7358.188266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7360.108272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7360.548295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7362.468262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7362.844293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7364.764264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7365.460135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7367.380267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7367.980130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7369.900161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7371.140171] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7373.060065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7373.436234] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7375.356253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7375.988233] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7377.908270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7378.748191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7380.796260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7381.236289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7383.412258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7384.316086] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7386.364262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7387.172093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7389.220046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7389.692283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7391.616100] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7391.960244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7394.008072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7394.768089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7396.944080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7397.256185] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7399.176090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7399.840081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7402.016103] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7402.424181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7404.600221] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7405.008117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7407.056056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7407.704302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7409.880070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7410.352202] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7412.408065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7413.204153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7414.253313] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 7414.254708] SGI XFS Quota Management subsystem
[ 7414.286200] JFS: nTxBlock = 8192, nTxLock = 65536
[ 7414.314786] NTFS driver 2.1.30 [Flags: R/O MODULE].
[ 7414.351231] QNX4 filesystem 0.2.3 registered.
[ 7414.417690] Btrfs loaded
[ 7415.276052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7415.588106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7417.516094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7418.472285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7420.648261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7421.296101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7423.472261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7424.008306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7425.928263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7427.136296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7429.336107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7429.780293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7431.960106] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7433.940185] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7435.988263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7437.084269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7439.152227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7440.624288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7442.928250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7443.480131] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7445.660056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7446.932286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7449.108262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7450.076279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7452.124079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7452.724144] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7454.900255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7456.028101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7458.076087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7458.392291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7460.572251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7462.196164] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7464.500144] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7465.276181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7467.452078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7468.036288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7470.212047] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7470.652071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7472.700076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7473.252295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7475.304085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7476.368298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7478.544265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7478.856260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7480.904266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7481.744290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7483.792086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7484.104238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7486.284266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7486.788237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7488.964084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7489.308112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7491.228077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7492.388252] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7494.500131] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7496.112195] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7498.288070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7498.840088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7501.020061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7501.716248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7503.636265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7504.380293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7506.428269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7506.836233] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7508.756268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7510.676270] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7510.860277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7513.164080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7513.812093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7515.864056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7516.512268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7518.560263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7519.864088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7521.912254] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7522.944110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7525.124142] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7525.676187] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7527.852231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7529.380298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7531.588116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7532.396290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7534.572263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7535.384198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7537.432072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7537.768297] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7538.348245] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7540.524088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7541.332292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7543.508175] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7544.476298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7546.656261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7547.848198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7549.896243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7550.208269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7552.256270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7552.840302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7555.016104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7555.552166] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7557.728192] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7558.440124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7560.616090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7560.928104] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7563.104265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7563.640096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7565.820187] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7566.164299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7568.500271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7569.756285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7571.932262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7572.676264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7575.140230] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7576.236277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7578.764292] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7579.988305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7582.164147] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7582.812295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7585.116116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7585.732172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7587.908054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7588.716103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7590.892266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7591.572159] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7593.844264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7595.132267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7597.308260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7598.228298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7600.408272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7601.728299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7604.000277] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7604.680114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7606.860109] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7607.412292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7609.588274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7610.364271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7612.540218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7613.412068] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7615.876080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7617.068103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7619.376200] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7620.376138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7623.032259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7624.640080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7626.816262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7628.616299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7630.984117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7631.536080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7633.844063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7635.324098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7637.532081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7637.772275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7638.256161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7640.436177] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7641.564278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7643.676264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7645.380118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7647.556075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7648.268154] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7650.572207] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7652.308295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7654.676051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7655.676113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7657.916265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7658.628295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7660.872109] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7661.488290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7663.664265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7665.208088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7667.420049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7668.100102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7670.692085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7671.372152] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7673.548272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7674.996250] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7677.204085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7678.268112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7680.572072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7681.284236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7683.460233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7684.684288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7687.148258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7687.928083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7690.488089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7691.392282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7693.696071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7694.440293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7696.616261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7697.168070] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7699.408070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7700.248104] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7702.552179] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7703.840079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7706.016092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7706.260250] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7706.808247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7709.372072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7711.536101] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7711.720265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7713.964070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7715.704289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7717.944223] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7718.592107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7721.088092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7721.360263] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7721.748106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7724.504084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7726.016076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7728.196209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7728.812295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7731.472104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7732.796259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7734.972264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7735.212080] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7735.696243] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7738.008136] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7738.564098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7740.804111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7741.044059] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7741.496108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7743.676059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7744.964052] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7747.304260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7747.952076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7750.256099] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7750.808113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7753.152053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7753.392235] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7754.648264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7756.984041] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7757.256272] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7757.996111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7760.208052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7761.400119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7763.640046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7764.480295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7766.656063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7767.336131] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7769.896132] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7771.124165] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7773.300193] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7773.980175] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7776.444045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7777.476280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7780.140263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7780.820176] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7783.060261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7783.612135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7785.820045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7786.692090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7788.872272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7789.872090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7792.048248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7792.600296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7794.808244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7795.680259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7798.016072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7798.920295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7801.512064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7802.608172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7804.788040] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7805.404278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7807.612252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7810.124218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7811.316310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7813.844258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7815.168293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7817.344079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7818.216113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7820.776107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7821.456108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7823.632080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7824.668300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7827.068278] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7828.708266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7830.888250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7831.728196] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7833.904195] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7834.208181] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7834.596229] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7836.772263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7837.516293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7839.564265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7840.132102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7842.372267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7843.244288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7845.676263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7846.740295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7849.108231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7850.972277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7853.244269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7854.372293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7856.548064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7856.788282] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7857.340307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7859.776038] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7860.424301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7862.600146] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7863.184160] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7865.360187] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7865.976116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7868.152117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7868.720269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7870.896246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7871.512267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7873.688257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7875.168261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7877.344111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7877.928116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7880.104239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7881.136292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7883.312262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7883.944283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7886.120269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7886.704287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7889.008269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7890.296310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7892.632269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7893.520121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7895.920186] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7896.728153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7899.068262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7901.348266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7903.684267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7904.460284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7906.700236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7907.284294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7909.524232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7911.516299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7913.788096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7914.564288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7916.748266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7917.300300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7919.508080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7920.064092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7922.528251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7923.624295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7925.800086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7926.480200] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7928.656056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7930.008115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7932.248213] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7932.864090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7935.104260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7935.344280] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7936.180268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7938.228094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7938.876094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7941.340088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7942.212099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7944.388260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7944.940288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7947.116106] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7947.924294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7950.132257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7950.812101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7953.084249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7953.700289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7955.844120] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7958.484086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7960.644263] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7960.828282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7963.164260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7964.452285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7966.692248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7967.660267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7969.836232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7971.028137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7973.204261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7973.548249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7975.728269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7976.600307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7979.064270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7979.744290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7981.920058] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7982.888306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7985.064236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7985.616183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7987.792167] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7988.032085] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7988.356235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7990.536255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7991.888114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7994.064271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7996.216290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7998.392089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7999.200302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8001.508241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8002.636102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8004.812074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8005.364235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8007.988096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8009.116156] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8011.392051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8012.008100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8014.060062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8015.348117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8017.620164] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8018.620193] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8020.796068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8021.476102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8023.652107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8024.908295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8027.084060] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8028.632084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8030.808081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8031.364294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8033.604238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8034.316089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8036.558082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8037.108058] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8039.284236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8040.028107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8042.076070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8043.028291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8045.204226] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8046.076264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8048.124069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8048.836115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8051.012246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8051.628092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8053.808271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8054.616288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8056.984264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8057.568297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8059.744263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8060.456189] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8062.696251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8063.312291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8065.360263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8066.200111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8068.632214] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8069.280135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8071.624245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8072.208090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8074.736237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8074.976082] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8075.560299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8078.568164] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8079.664181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8082.288048] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8083.064186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8085.272097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8085.920272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8088.096224] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8090.024095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8092.200263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8093.008094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8095.316071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8095.868094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8098.044048] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8098.660293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8101.092063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8101.740134] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8103.916065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8104.980100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8107.156271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8107.836121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8110.048049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8110.760177] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8112.936093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8114.064265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8116.432085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8117.624089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8119.800271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8120.352092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8122.528273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8124.104301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8126.280269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8126.960102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8129.136271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8130.040286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8132.536268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8133.248079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8135.488068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8136.392297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8138.600065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8139.312172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8141.488158] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8142.200074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8144.376209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8145.184071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8147.360262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8148.328270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8150.632253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8151.856292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8154.096273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8154.808291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8156.984132] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8157.760107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8160.160262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8161.192284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8163.464266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8164.368145] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8166.832042] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8167.704275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8170.392070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8171.008198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8173.188162] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8173.836090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8176.152063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8177.920285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8180.224074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8180.904298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8183.080064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8184.144100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8186.480201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8188.444265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8190.748056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8191.812074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8193.988105] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8194.636172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8196.844173] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8197.684296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8200.212267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8201.020191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8203.360041] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8203.912219] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8206.216260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8207.216291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8209.456081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8210.232275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8212.408262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8213.152280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8215.396232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8216.300271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8218.476077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8219.092295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8221.268263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8222.108137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8224.732095] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8225.444091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8227.620227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8228.332115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8230.508238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8231.444298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8233.876154] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8234.748124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8236.956232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8237.572116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8239.748054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8240.524278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8242.704077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8243.384293] hub 8-0:1.0: unable to enumerate USB device on port 2
ounce failed, port 3 disabled
[ 6929.824292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6931.748097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6932.060294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6934.108252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6934.420296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6936.468080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6936.844130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6938.764055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6939.812209] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6942.020199] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6942.396137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6944.316251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6944.628266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6946.552263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6947.472286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6949.392264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6950.572280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6952.492261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6952.964301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6955.012059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6956.220292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6958.140260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6958.452107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6960.372269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6960.716099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6962.892268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6963.204146] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6965.128257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6965.440305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6967.360086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6967.864294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6969.784121] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6970.960125] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6972.880194] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6973.704248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6975.624269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6976.800286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6978.720053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6979.032182] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6980.952266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6981.264282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6983.184255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6983.624288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6985.704076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6986.016101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6987.936259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6988.536300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6990.456252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6991.440280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6993.360268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6994.056289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6995.976264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6996.416294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6998.336255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 6998.904077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7000.832169] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7001.656163] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7003.576107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7004.144244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7006.064256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7006.376289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7008.296260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7008.960263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7010.880284] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7011.608294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7013.528259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7014.096292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7016.020081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7016.332167] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7018.252243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7018.724307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7020.644271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7021.116074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7023.036059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7023.892101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7025.816220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7026.288289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7028.208079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7028.840285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7030.760258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7031.072195] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7032.996124] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7033.724188] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7035.644237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7035.956096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7037.876050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7038.444100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7040.364061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7040.804296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7042.724081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7043.836119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7045.756272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7046.068120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7047.988091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7048.300260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7050.224076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7050.568296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7052.488268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7052.800267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7054.724249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7055.036080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7056.956260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7057.492273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7059.412089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7059.852275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7061.772145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7063.076092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7064.996157] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7065.596244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7067.516091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7067.924249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7069.844121] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7071.052269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7072.972067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7073.348268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7075.268100] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7075.612103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7077.532265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7077.844275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7079.764093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7080.076065] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7081.996243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7082.372292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7084.292231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7084.924300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7086.844265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7087.156117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7089.076264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7090.996084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7091.372288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7093.292160] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7094.244169] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7096.164201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7096.988154] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7098.908272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7099.572299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7101.492265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7102.284296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7104.204267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7104.804289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7106.724045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7107.068065] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7108.988101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7109.300097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7111.220073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7111.532278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7113.452243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7113.764298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7115.684063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7116.092285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7118.012045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7118.644126] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7120.568050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7120.912111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7122.832070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7123.304083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7125.224157] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7126.432209] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7128.352087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7128.664114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7130.584248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7131.056121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7132.976248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7133.416113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7135.336052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7136.032277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7137.952238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7138.520100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7140.440066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7140.976290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7142.896265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7143.272090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7145.192260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7145.600291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7147.524061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7148.060101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7149.980256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7150.580095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7152.500260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7152.908304] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7154.828263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7155.524168] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7157.444080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7157.820238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7159.740232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7160.180236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7162.100056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7162.604109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7164.524264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7164.836100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7166.756216] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7167.424124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7169.344116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7170.040267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7171.960042] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7172.272241] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7174.192078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7175.048082] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7176.968074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7177.568263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7179.488054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7179.800084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7181.976190] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7182.544074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7184.464086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7184.904119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7186.824125] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7187.140183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7189.060220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7189.372246] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7191.292046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7191.732085] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7193.652232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7194.124291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7196.044127] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7196.964292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7198.884208] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7199.644295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7201.568240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7201.880291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7203.800265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7204.176103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7206.096233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7207.240109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7209.160274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7209.568264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7211.488262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7212.408249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7214.328238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7214.640295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7216.560086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7217.384173] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7219.432069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7219.840237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7221.760081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7222.264270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7224.184273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7224.496302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7226.424264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7226.928097] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7228.848237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7229.160150] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7231.084060] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7231.528275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7233.448256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7234.272071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7236.192214] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7236.824105] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7238.744241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7239.120087] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7241.040052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7241.384081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7243.304137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7245.224249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7245.984259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7247.904053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7248.696165] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7250.616220] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7250.992237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7252.912256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7253.704281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7255.628111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7256.100305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7258.020253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7258.332268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7260.252057] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7260.568109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7262.616111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7263.456293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7265.504050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7266.120297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7268.296265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7269.056279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7270.976242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7271.608298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7273.528229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7274.992273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7276.912264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7277.512192] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7279.432156] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7280.000161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7281.920241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7282.264276] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7284.184086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7284.720255] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7286.640256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7287.016299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7288.936289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7289.248310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7291.168265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7291.704294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7293.624089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7293.936268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7295.860262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7296.364302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7298.284092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7298.756286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7300.804257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7301.484125] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7303.532130] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7303.876160] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7305.928083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7306.560119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7308.488098] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7309.152132] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7311.080131] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7312.592153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7314.512127] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7314.888127] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7316.812152] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7317.284166] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7319.368289] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7321.184152] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7323.360130] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7324.392162] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7326.316139] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7326.820135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7328.740111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7329.244157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7331.292101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7331.668158] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7333.588092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7334.636157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7336.556102] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7337.652138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7339.708136] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7340.260077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7342.308126] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7343.132113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7345.052243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7345.364298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7347.284239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7348.364294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7350.284269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7350.916289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7352.964069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7353.308303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7355.484242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7355.956115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7357.876183] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7358.188266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7360.108272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7360.548295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7362.468262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7362.844293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7364.764264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7365.460135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7367.380267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7367.980130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7369.900161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7371.140171] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7373.060065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7373.436234] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7375.356253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7375.988233] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7377.908270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7378.748191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7380.796260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7381.236289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7383.412258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7384.316086] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7386.364262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7387.172093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7389.220046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7389.692283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7391.616100] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7391.960244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7394.008072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7394.768089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7396.944080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7397.256185] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7399.176090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7399.840081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7402.016103] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7402.424181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7404.600221] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7405.008117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7407.056056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7407.704302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7409.880070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7410.352202] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7412.408065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7413.204153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7414.253313] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 7414.254708] SGI XFS Quota Management subsystem
[ 7414.286200] JFS: nTxBlock = 8192, nTxLock = 65536
[ 7414.314786] NTFS driver 2.1.30 [Flags: R/O MODULE].
[ 7414.351231] QNX4 filesystem 0.2.3 registered.
[ 7414.417690] Btrfs loaded
[ 7415.276052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7415.588106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7417.516094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7418.472285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7420.648261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7421.296101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7423.472261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7424.008306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7425.928263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7427.136296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7429.336107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7429.780293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7431.960106] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7433.940185] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7435.988263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7437.084269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7439.152227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7440.624288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7442.928250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7443.480131] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7445.660056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7446.932286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7449.108262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7450.076279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7452.124079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7452.724144] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7454.900255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7456.028101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7458.076087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7458.392291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7460.572251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7462.196164] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7464.500144] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7465.276181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7467.452078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7468.036288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7470.212047] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7470.652071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7472.700076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7473.252295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7475.304085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7476.368298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7478.544265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7478.856260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7480.904266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7481.744290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7483.792086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7484.104238] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7486.284266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7486.788237] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7488.964084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7489.308112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7491.228077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7492.388252] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7494.500131] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7496.112195] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7498.288070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7498.840088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7501.020061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7501.716248] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7503.636265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7504.380293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7506.428269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7506.836233] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7508.756268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7510.676270] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7510.860277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7513.164080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7513.812093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7515.864056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7516.512268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7518.560263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7519.864088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7521.912254] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7522.944110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7525.124142] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7525.676187] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7527.852231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7529.380298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7531.588116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7532.396290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7534.572263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7535.384198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7537.432072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7537.768297] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7538.348245] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7540.524088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7541.332292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7543.508175] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7544.476298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7546.656261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7547.848198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7549.896243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7550.208269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7552.256270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7552.840302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7555.016104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7555.552166] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7557.728192] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7558.440124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7560.616090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7560.928104] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7563.104265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7563.640096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7565.820187] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7566.164299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7568.500271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7569.756285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7571.932262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7572.676264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7575.140230] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7576.236277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7578.764292] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7579.988305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7582.164147] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7582.812295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7585.116116] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7585.732172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7587.908054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7588.716103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7590.892266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7591.572159] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7593.844264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7595.132267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7597.308260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7598.228298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7600.408272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7601.728299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7604.000277] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7604.680114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7606.860109] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7607.412292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7609.588274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7610.364271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7612.540218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7613.412068] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7615.876080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7617.068103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7619.376200] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7620.376138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7623.032259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7624.640080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7626.816262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7628.616299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7630.984117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7631.536080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7633.844063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7635.324098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7637.532081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7637.772275] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7638.256161] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7640.436177] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7641.564278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7643.676264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7645.380118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7647.556075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7648.268154] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7650.572207] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7652.308295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7654.676051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7655.676113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7657.916265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7658.628295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7660.872109] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7661.488290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7663.664265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7665.208088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7667.420049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7668.100102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7670.692085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7671.372152] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7673.548272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7674.996250] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7677.204085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7678.268112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7680.572072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7681.284236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7683.460233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7684.684288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7687.148258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7687.928083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7690.488089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7691.392282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7693.696071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7694.440293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7696.616261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7697.168070] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7699.408070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7700.248104] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7702.552179] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7703.840079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7706.016092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7706.260250] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7706.808247] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7709.372072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7711.536101] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7711.720265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7713.964070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7715.704289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7717.944223] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7718.592107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7721.088092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7721.360263] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7721.748106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7724.504084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7726.016076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7728.196209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7728.812295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7731.472104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7732.796259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7734.972264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7735.212080] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7735.696243] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7738.008136] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7738.564098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7740.804111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7741.044059] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7741.496108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7743.676059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7744.964052] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7747.304260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7747.952076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7750.256099] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7750.808113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7753.152053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7753.392235] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7754.648264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7756.984041] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7757.256272] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7757.996111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7760.208052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7761.400119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7763.640046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7764.480295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7766.656063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7767.336131] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7769.896132] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7771.124165] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7773.300193] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7773.980175] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7776.444045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7777.476280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7780.140263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7780.820176] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7783.060261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7783.612135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7785.820045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7786.692090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7788.872272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7789.872090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7792.048248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7792.600296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7794.808244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7795.680259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7798.016072] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7798.920295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7801.512064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7802.608172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7804.788040] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7805.404278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7807.612252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7810.124218] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7811.316310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7813.844258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7815.168293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7817.344079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7818.216113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7820.776107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7821.456108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7823.632080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7824.668300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7827.068278] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7828.708266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7830.888250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7831.728196] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7833.904195] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7834.208181] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7834.596229] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7836.772263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7837.516293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7839.564265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7840.132102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7842.372267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7843.244288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7845.676263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7846.740295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7849.108231] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7850.972277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7853.244269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7854.372293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7856.548064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7856.788282] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7857.340307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7859.776038] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7860.424301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7862.600146] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7863.184160] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7865.360187] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7865.976116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7868.152117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7868.720269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7870.896246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7871.512267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7873.688257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7875.168261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7877.344111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7877.928116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7880.104239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7881.136292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7883.312262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7883.944283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7886.120269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7886.704287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7889.008269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7890.296310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7892.632269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7893.520121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7895.920186] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7896.728153] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7899.068262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7901.348266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7903.684267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7904.460284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7906.700236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7907.284294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7909.524232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7911.516299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7913.788096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7914.564288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7916.748266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7917.300300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7919.508080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7920.064092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7922.528251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7923.624295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7925.800086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7926.480200] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7928.656056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7930.008115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7932.248213] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7932.864090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7935.104260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7935.344280] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7936.180268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7938.228094] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7938.876094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7941.340088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7942.212099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7944.388260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7944.940288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7947.116106] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7947.924294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7950.132257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7950.812101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7953.084249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7953.700289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7955.844120] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7958.484086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7960.644263] hub 8-0:1.0: connect-debounce failed, port 1 disabled
[ 7960.828282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7963.164260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7964.452285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7966.692248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7967.660267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7969.836232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7971.028137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7973.204261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7973.548249] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7975.728269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7976.600307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7979.064270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7979.744290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7981.920058] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7982.888306] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7985.064236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7985.616183] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7987.792167] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7988.032085] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 7988.356235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7990.536255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7991.888114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7994.064271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7996.216290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 7998.392089] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 7999.200302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8001.508241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8002.636102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8004.812074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8005.364235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8007.988096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8009.116156] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8011.392051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8012.008100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8014.060062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8015.348117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8017.620164] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8018.620193] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8020.796068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8021.476102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8023.652107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8024.908295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8027.084060] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8028.632084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8030.808081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8031.364294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8033.604238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8034.316089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8036.558082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8037.108058] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8039.284236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8040.028107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8042.076070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8043.028291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8045.204226] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8046.076264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8048.124069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8048.836115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8051.012246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8051.628092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8053.808271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8054.616288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8056.984264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8057.568297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8059.744263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8060.456189] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8062.696251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8063.312291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8065.360263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8066.200111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8068.632214] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8069.280135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8071.624245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8072.208090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8074.736237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8074.976082] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8075.560299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8078.568164] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8079.664181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8082.288048] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8083.064186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8085.272097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8085.920272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8088.096224] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8090.024095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8092.200263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8093.008094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8095.316071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8095.868094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8098.044048] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8098.660293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8101.092063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8101.740134] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8103.916065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8104.980100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8107.156271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8107.836121] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8110.048049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8110.760177] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8112.936093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8114.064265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8116.432085] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8117.624089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8119.800271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8120.352092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8122.528273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8124.104301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8126.280269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8126.960102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8129.136271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8130.040286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8132.536268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8133.248079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8135.488068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8136.392297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8138.600065] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8139.312172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8141.488158] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8142.200074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8144.376209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8145.184071] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8147.360262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8148.328270] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8150.632253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8151.856292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8154.096273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8154.808291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8156.984132] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8157.760107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8160.160262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8161.192284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8163.464266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8164.368145] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8166.832042] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8167.704275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8170.392070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8171.008198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8173.188162] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8173.836090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8176.152063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8177.920285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8180.224074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8180.904298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8183.080064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8184.144100] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8186.480201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8188.444265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8190.748056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8191.812074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8193.988105] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8194.636172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8196.844173] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8197.684296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8200.212267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8201.020191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8203.360041] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8203.912219] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8206.216260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8207.216291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8209.456081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8210.232275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8212.408262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8213.152280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8215.396232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8216.300271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8218.476077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8219.092295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8221.268263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8222.108137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8224.732095] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8225.444091] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8227.620227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8228.332115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8230.508238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8231.444298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8233.876154] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8234.748124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8236.956232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8237.572116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8239.748054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8240.524278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8242.704077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8243.384293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8245.656274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8246.432096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8248.704260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8249.608235] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8251.880046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8252.912075] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8255.412243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8256.252300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8259.388272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8260.296261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8262.728074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8264.208130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8266.480201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8266.720222] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8267.332255] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8269.572263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8270.124096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8272.364266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8272.980173] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8275.284055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8275.524070] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8275.980074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8278.448274] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8279.352233] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8282.716263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8283.268234] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8285.860042] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8287.276293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8289.548271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8290.100236] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8292.276107] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8292.956120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8295.196051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8295.876223] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8298.148070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8300.044074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8302.348252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8303.444296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8305.620240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8306.364293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8308.572049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8309.700253] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8312.132262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8312.972103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8315.820235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8316.884065] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8319.156236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8319.708113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8322.140102] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8323.524077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8326.020145] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8326.924202] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8329.484255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8330.132292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8332.728245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8332.968257] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8333.292250] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8335.692080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8337.044291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8339.384149] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8340.384294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8342.848045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8343.592102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8346.120243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8347.376289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8350.704232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8351.136257] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8351.844287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8354.020086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8355.180191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8357.420166] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8358.004223] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8360.308270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8361.276280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8363.452243] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8364.036268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8366.436262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8367.564128] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8370.156258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8371.316277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8373.588070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8374.652303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8376.956264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8377.196074] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8377.584297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8380.816294] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8381.368282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8383.832235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8384.576114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8387.492146] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8388.588130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8390.960264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8391.512089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8393.816238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8394.400291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8396.576244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8397.128107] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8399.368075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8399.984281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8402.516253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8403.068074] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8405.404253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8408.396210] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8409.652120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8412.084151] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8412.732301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8415.132077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8415.812101] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8418.404096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8419.660103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8422.188264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8422.964282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8425.396261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8426.172090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8428.348242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8429.124114] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8431.428051] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8432.684090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8434.860222] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8436.628303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8438.900271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8439.900301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8442.076064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8443.204090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8445.956269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8446.764300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8449.580086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8450.196079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8452.372245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8453.020293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8455.260268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8455.908280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8458.084209] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8458.420280] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8458.948297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8461.348066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8461.900286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8464.108261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8464.348266] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8465.760303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8468.032235] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8468.936279] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8471.208252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8471.984310] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8474.160052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8475.128267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8477.880044] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8478.816102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8481.184078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8481.896239] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8484.264070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8485.040083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8487.604264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8488.188094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8490.844260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8491.620316] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8493.892267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8494.604275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8496.784046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8497.336092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8499.928043] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8500.864085] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8503.232097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8503.848098] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8506.056199] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8507.088292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8509.264061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8510.136096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8512.344148] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8513.120256] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8515.680064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8516.520278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8518.696234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8519.504289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8521.744244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8523.576106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8525.752267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8526.432123] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8528.608248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8529.160108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8531.816081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8533.008272] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8535.984076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8536.760292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8538.936092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8539.904095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8542.528117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8543.688113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8545.864260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8546.736274] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8548.944240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8549.528136] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8552.088241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8552.864077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8555.620087] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8556.716138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8559.660076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8560.660298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8563.732266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8565.020112] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8567.196261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8568.164296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8570.500126] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8570.740185] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8571.128144] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8573.368181] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8573.984201] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8576.192247] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8577.384271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8579.688057] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8580.784096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8583.248260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8583.800155] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8585.984063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8587.240278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8589.736261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8590.544281] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8592.816240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8593.688296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8595.864103] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8596.200245] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8596.748297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8598.924234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8599.476293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8601.748171] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8603.324186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8605.756234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8606.404288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8609.092271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8609.900259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8612.236262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8613.172290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8615.444263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8616.220271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8618.428255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8619.364295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8621.540134] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8622.092302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8624.396273] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8625.140300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8627.316263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8628.700116] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8630.876238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8631.556296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8633.764150] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8634.380193] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8636.812241] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8637.844289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8640.948268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8641.628252] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8643.964117] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8644.548286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8646.724266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8646.964272] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 8649.152261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8650.216300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8652.392277] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8653.136303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8655.316255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8656.252297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8658.556259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8659.396283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8661.860264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8662.476283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8664.780141] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8666.100231] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8668.276228] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8668.924099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8671.260256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8671.812254] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8673.988272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8674.668126] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8676.844255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8677.972291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8680.276255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8681.404291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8683.580261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8684.132293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8686.308262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8687.244266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8689.420258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8690.200131] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8692.728267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8693.728186] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8695.904108] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8696.456108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8698.632249] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8699.184117] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8701.360259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8701.960293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8704.136256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8705.136295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8707.312265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8707.960303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8710.136257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8710.688284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8712.992233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8713.544301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8715.752232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8716.368288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8718.672262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8719.752299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8721.928258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8722.480287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8724.656163] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8725.688145] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8727.896200] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8729.088273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8731.264261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8732.760283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8734.904267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8735.440301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8737.488256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8738.840302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8741.016260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8741.664271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8743.904068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8744.456277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8746.632245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8747.344299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8749.392262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8749.976286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8752.024260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8752.576292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8754.752262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8755.304189] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8757.480155] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8758.992242] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8761.168268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8762.456135] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8764.632260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8765.536293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8767.584252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8768.392302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8770.568267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8771.040286] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8773.088250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8773.496283] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8775.416266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8776.016289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8778.064263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8778.440105] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8780.364247] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8780.676298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8782.724154] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8783.036300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8785.084256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8785.620119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8787.668148] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8788.140179] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8790.188229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8790.820266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8792.868088] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8793.244266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8795.292265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8796.164302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8798.212258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8798.652292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8800.828222] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8801.460290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8803.508070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8804.236284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8806.156109] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8806.660292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8808.708265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8809.676126] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8811.728075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8812.296305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8814.344201] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8814.656282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8816.704177] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8817.432190] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8819.352177] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8819.760211] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8821.680091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8823.176259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8825.352257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8825.728323] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8827.648256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8828.120293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8830.040057] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8830.576157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8832.496086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8833.000307] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8834.920069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8835.232295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8837.408121] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8837.720298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8839.640265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8839.984265] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8842.164111] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8842.636266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8844.556269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8844.932295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8846.852050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8847.420132] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8849.340154] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8849.652187] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8851.572212] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8851.884252] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8853.932266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8855.852256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8856.260297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8858.180054] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8859.228213] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8861.148055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8861.524154] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8863.572052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8864.124082] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8866.044062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8866.420259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8868.340058] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8869.036294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8870.956268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8871.492079] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8873.544080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8874.304296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8876.224269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8876.536291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8878.712063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8879.088188] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8881.136176] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8881.512205] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8883.432198] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8883.744291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8885.668258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8886.044292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8887.964261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8888.980113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8890.900070] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8891.340099] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8893.388179] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8894.308290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8896.228090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8896.604129] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8898.524258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8899.060119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8900.984095] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8901.296118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8903.216149] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8905.504268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8905.880288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8907.800166] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8908.304102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8910.224126] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8910.792178] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8912.712191] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8913.088206] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8915.008060] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8915.512289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8917.432261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8917.872298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8919.792259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8920.296299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8922.216222] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8922.624301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8924.544263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8924.856297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8926.780272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8927.284089] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8929.204093] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8929.548291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8931.468086] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8931.940296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8933.860169] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8934.332296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8936.252260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8936.628294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8938.676245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8938.988102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8940.912103] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8941.224158] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8943.148137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8943.652092] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8945.704095] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8946.592157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8948.512271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8948.824244] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8950.748080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8951.252288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8953.172124] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8954.060294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8956.108222] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8956.868280] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8958.788258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8959.132264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8961.052068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8961.524287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8963.444269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8964.252291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8966.300259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8966.708138] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8968.628255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8969.100095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8971.148161] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8971.588197] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8973.508170] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8973.820148] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8975.740244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8976.052299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8978.100264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8978.956290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8981.008268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8981.320291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8983.240259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8983.552095] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8985.476264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8986.556119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8988.476226] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8988.884319] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8990.804071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8991.148300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8993.196246] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8993.668087] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8995.588261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8996.060301] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 8997.980251] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 8998.964287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9000.884248] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9001.260203] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9003.180137] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9005.104194] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9005.512253] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9007.432230] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9007.840282] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9009.760278] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9010.456298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9012.376232] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9012.720292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9014.640270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9015.112289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9017.032294] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9017.632137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9019.552097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9020.216284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9022.264260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9022.576109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9024.496264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9025.096267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9027.016271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9027.328264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9029.248258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9029.560298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9031.608139] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9032.112157] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9034.160151] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9034.792203] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9036.712225] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9037.024267] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9039.072237] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9039.384302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9041.304260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9043.480266] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9043.952080] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9045.872272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9046.376264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9048.296056] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9048.896111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9050.816233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9051.192302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9053.112140] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9053.872081] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9055.796256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9056.108090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9058.028059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9058.340087] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9060.260271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9060.572093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9062.492234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9063.092199] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9065.012047] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9065.708103] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9067.628233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9068.324110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9070.244263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9070.876264] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9072.796092] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9073.652266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9075.576108] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9075.888119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9077.808253] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9078.120292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9080.044059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9080.548106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9082.468076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9082.972299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9084.892059] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9085.204108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9087.124262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9087.436109] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9089.356082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9090.468291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9092.388097] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9093.436299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9095.356134] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9096.020182] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9097.940229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9098.316259] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9100.368262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9100.936294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9102.856252] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9103.232276] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9105.152265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9105.688298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9107.608270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9108.048293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9109.968256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9110.568263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9112.488259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9112.992302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9114.912250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9115.704288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9117.624258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9118.192295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9120.112234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9120.520261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9122.440263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9122.752295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9124.672068] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9124.984108] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9126.904162] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9128.368118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9130.292256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9130.668299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9132.588098] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9132.900269] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9134.820265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9135.356299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9137.276244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9137.588296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9139.512064] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9139.824105] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9141.744080] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9142.056289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9143.976271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9144.704285] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9146.624074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9147.032273] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9148.952223] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9149.296156] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9151.216265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9153.136271] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9153.608090] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9155.528077] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9156.000198] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9157.920040] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9158.392084] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9160.316045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9160.660295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9162.580236] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9163.148240] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9165.068053] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9165.380298] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9167.300081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9167.676225] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9169.596346] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9170.100292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9172.020079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9173.100299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9175.152078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9175.688066] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9177.608081] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9177.952078] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9179.872270] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9180.472111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9182.392307] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9183.504297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9185.424245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9185.736102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9187.916118] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9188.228181] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9190.148221] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9192.068073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9192.860261] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9195.036090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9195.716147] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9197.640090] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9198.016309] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9200.192040] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9200.536290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9202.456287] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9202.992292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9205.040050] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9205.416268] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9207.336115] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9208.160266] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9210.084245] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9210.396192] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9212.444265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9212.884070] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9214.804061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9215.564078] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9217.484076] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9218.196115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9220.244074] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9220.556232] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9222.604091] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9222.916294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9225.092229] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9226.236294] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9228.284269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9228.868083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9230.920256] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9231.552172] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9233.600268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9234.584119] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9236.504075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9236.816106] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9238.868238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9239.500300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9241.548239] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9242.196133] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9244.372233] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9245.452263] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9247.372073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9247.972190] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9250.148167] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9250.748196] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9252.672126] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9253.480297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9255.784261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9256.528300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9258.704055] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9260.008086] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9262.184242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9262.976289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9265.152227] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9265.864076] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9268.040250] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9268.720120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9270.896046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9271.240094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9273.384151] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9274.320288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9276.496267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9277.048289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9279.100115] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9279.604164] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9281.652052] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9283.296096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9285.472114] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9286.952271] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9289.128260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9289.792291] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9291.968255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9292.520137] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9294.824230] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9295.440295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9297.648083] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9298.424305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9300.608262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9301.160260] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9303.432257] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9303.672278] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 9304.796105] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9306.972238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9308.020123] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9310.196255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9310.908122] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9313.180214] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9314.532096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9316.708078] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9317.324159] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9319.532263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9320.344221] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9322.392114] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9322.944149] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9325.160104] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9325.904297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9328.080066] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9328.824083] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9330.940073] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9331.588305] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9334.020216] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9334.764289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9336.944268] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9337.496296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9340.024045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9340.768142] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9343.040049] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9344.136130] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9346.536242] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9347.088288] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9349.268264] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9349.740102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9351.948262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9352.788290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9355.028174] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9357.084073] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9359.580255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9361.092293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9363.268259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9363.820120] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9365.996234] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9367.060284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9369.684269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9370.268295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9372.444143] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9373.188189] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9375.364101] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9375.604096] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 9376.760296] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9378.936075] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9379.744284] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9381.920263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9383.272297] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9385.448079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9386.032292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9388.304258] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9389.048293] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9391.224079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9391.968113] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9394.144133] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9394.952166] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9397.128262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9397.712220] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9400.016079] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9400.888277] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9403.096046] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9404.128371] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9406.176195] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9406.520111] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9408.696045] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9409.696093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9411.872071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9413.320275] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9415.464084] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9415.936295] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9417.984260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9419.176302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9421.352240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9422.000311] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9424.176261] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9424.776088] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9426.984255] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9427.568318] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9429.744265] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9430.552096] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9432.728144] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9433.280078] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9435.456069] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9435.832077] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9438.008062] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9438.592093] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9440.640082] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9441.192124] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9443.496061] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9443.736071] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 9444.668094] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9446.880269] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9447.432115] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9449.608244] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9450.224141] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9452.272272] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9452.888118] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9455.388260] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9456.068300] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9458.340267] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9459.436287] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9461.680240] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9462.776110] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9464.952096] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9465.632191] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9467.808067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9468.680290] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9471.180067] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9472.948302] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9475.284071] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9475.932289] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9478.108263] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9478.420319] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9480.596221] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9481.788087] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9483.932262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9484.708155] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9486.884279] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9487.436299] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9489.616262] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9490.520278] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9493.880102] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9494.120127] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 9494.540173] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9496.716173] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9497.332102] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9499.508259] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9499.820292] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9501.996238] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9502.612303] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 9504.916063] hub 2-0:1.0: connect-debounce failed, port 3 disabled
[ 9505.692133] hub 8-0:1.0: unable to enumerate USB device on port 2

```
The file kern-old.txt is 13,000 lines long and 2.4 MB large. Even copying it in here in bits and pieces makes it timing out every time. Can't do it.
And here is Xorg.txt:
```

[    20.190] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    20.190] X Protocol Version 11, Revision 0
[    20.190] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    20.190] Current Operating System: Linux Robert-HP 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686
[    20.190] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=62d69c53-7b67-452c-b1d3-ad90c3181621 ro quiet splash vt.handoff=7
[    20.190] Build Date: 29 August 2012  12:10:05AM
[    20.190] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    20.190] Current version of pixman: 0.24.4
[    20.190]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.190] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.190] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 16 21:11:17 2012
[    20.204] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.205] (==) No Layout section.  Using the first Screen section.
[    20.205] (==) No screen section available. Using defaults.
[    20.205] (**) |-->Screen "Default Screen Section" (0)
[    20.205] (**) |   |-->Monitor "<default monitor>"
[    20.205] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.205] (==) Automatically adding devices
[    20.205] (==) Automatically enabling devices
[    20.205] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.205]     Entry deleted from font path.
[    20.205] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.205] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.205] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.205] (II) Loader magic: 0xb773a5a0
[    20.205] (II) Module ABI versions:
[    20.205]     X.Org ANSI C Emulation: 0.4
[    20.205]     X.Org Video Driver: 11.0
[    20.205]     X.Org XInput driver : 16.0
[    20.205]     X.Org Server Extension : 6.0
[    20.206] (--) PCI:*(0:0:2:0) 8086:2a42:103c:30dd rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x000060f0/8
[    20.206] (--) PCI: (0:0:2:1) 8086:2a43:103c:30dd rev 7, Mem @ 0x90400000/1048576
[    20.206] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.206] (II) LoadModule: "extmod"
[    20.213] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.214] (II) Module extmod: vendor="X.Org Foundation"
[    20.214]     compiled for 1.11.3, module version = 1.0.0
[    20.214]     Module class: X.Org Server Extension
[    20.214]     ABI class: X.Org Server Extension, version 6.0
[    20.214] (II) Loading extension MIT-SCREEN-SAVER
[    20.214] (II) Loading extension XFree86-VidModeExtension
[    20.214] (II) Loading extension XFree86-DGA
[    20.214] (II) Loading extension DPMS
[    20.214] (II) Loading extension XVideo
[    20.214] (II) Loading extension XVideo-MotionCompensation
[    20.214] (II) Loading extension X-Resource
[    20.214] (II) LoadModule: "dbe"
[    20.214] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.214] (II) Module dbe: vendor="X.Org Foundation"
[    20.214]     compiled for 1.11.3, module version = 1.0.0
[    20.214]     Module class: X.Org Server Extension
[    20.214]     ABI class: X.Org Server Extension, version 6.0
[    20.214] (II) Loading extension DOUBLE-BUFFER
[    20.214] (II) LoadModule: "glx"
[    20.214] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.214] (II) Module glx: vendor="X.Org Foundation"
[    20.214]     compiled for 1.11.3, module version = 1.0.0
[    20.214]     ABI class: X.Org Server Extension, version 6.0
[    20.214] (==) AIGLX enabled
[    20.214] (II) Loading extension GLX
[    20.214] (II) LoadModule: "record"
[    20.215] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.215] (II) Module record: vendor="X.Org Foundation"
[    20.215]     compiled for 1.11.3, module version = 1.13.0
[    20.215]     Module class: X.Org Server Extension
[    20.215]     ABI class: X.Org Server Extension, version 6.0
[    20.215] (II) Loading extension RECORD
[    20.215] (II) LoadModule: "dri"
[    20.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.215] (II) Module dri: vendor="X.Org Foundation"
[    20.215]     compiled for 1.11.3, module version = 1.0.0
[    20.215]     ABI class: X.Org Server Extension, version 6.0
[    20.215] (II) Loading extension XFree86-DRI
[    20.215] (II) LoadModule: "dri2"
[    20.216] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.216] (II) Module dri2: vendor="X.Org Foundation"
[    20.216]     compiled for 1.11.3, module version = 1.2.0
[    20.216]     ABI class: X.Org Server Extension, version 6.0
[    20.216] (II) Loading extension DRI2
[    20.216] (==) Matched intel as autoconfigured driver 0
[    20.216] (==) Matched vesa as autoconfigured driver 1
[    20.216] (==) Matched fbdev as autoconfigured driver 2
[    20.216] (==) Assigned the driver to the xf86ConfigLayout
[    20.216] (II) LoadModule: "intel"
[    20.216] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.216] (II) Module intel: vendor="X.Org Foundation"
[    20.216]     compiled for 1.11.3, module version = 2.17.0
[    20.216]     Module class: X.Org Video Driver
[    20.216]     ABI class: X.Org Video Driver, version 11.0
[    20.216] (II) LoadModule: "vesa"
[    20.216] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.217] (II) Module vesa: vendor="X.Org Foundation"
[    20.217]     compiled for 1.11.3, module version = 2.3.0
[    20.217]     Module class: X.Org Video Driver
[    20.217]     ABI class: X.Org Video Driver, version 11.0
[    20.217] (II) LoadModule: "fbdev"
[    20.217] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.217] (II) Module fbdev: vendor="X.Org Foundation"
[    20.217]     compiled for 1.11.3, module version = 0.4.2
[    20.217]     ABI class: X.Org Video Driver, version 11.0
[    20.217] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    20.217] (II) VESA: driver for VESA chipsets: vesa
[    20.217] (II) FBDEV: driver for framebuffer: fbdev
[    20.217] (++) using VT number 7

[    20.219] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.219] (WW) Falling back to old probe method for vesa
[    20.219] (WW) Falling back to old probe method for fbdev
[    20.219] (II) Loading sub module "fbdevhw"
[    20.219] (II) LoadModule: "fbdevhw"
[    20.233] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.233] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.233]     compiled for 1.11.3, module version = 0.0.2
[    20.233]     ABI class: X.Org Video Driver, version 11.0
[    20.234] drmOpenDevice: node name is /dev/dri/card0
[    20.234] drmOpenDevice: open result is 9, (OK)
[    20.234] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.234] drmOpenDevice: node name is /dev/dri/card0
[    20.234] drmOpenDevice: open result is 9, (OK)
[    20.234] drmOpenByBusid: drmOpenMinor returns 9
[    20.234] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.234] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.234] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.234] (==) intel(0): RGB weight 888
[    20.234] (==) intel(0): Default visual is TrueColor
[    20.234] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    20.234] (--) intel(0): Chipset: "GM45"
[    20.234] (**) intel(0): Relaxed fencing enabled
[    20.234] (**) intel(0): Wait on SwapBuffers? enabled
[    20.234] (**) intel(0): Triple buffering? enabled
[    20.234] (**) intel(0): Framebuffer tiled
[    20.234] (**) intel(0): Pixmaps tiled
[    20.234] (**) intel(0): 3D buffers tiled
[    20.234] (**) intel(0): SwapBuffers wait enabled
[    20.234] (==) intel(0): video overlay key set to 0x101fe
[    20.234] (II) intel(0): Output LVDS1 has no monitor section
[    20.234] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    20.256] (II) intel(0): Output VGA1 has no monitor section
[    20.260] (II) intel(0): Output HDMI1 has no monitor section
[    20.260] (II) intel(0): Output DP1 has no monitor section
[    20.308] (II) intel(0): Output DP2 has no monitor section
[    20.609] (II) intel(0): Output TV1 has no monitor section
[    20.609] (II) intel(0): EDID for output LVDS1
[    20.609] (II) intel(0): Manufacturer: LPL  Model: 3d01  Serial#: 0
[    20.609] (II) intel(0): Year: 2008  Week: 0
[    20.609] (II) intel(0): EDID Version: 1.3
[    20.609] (II) intel(0): Digital Display Input
[    20.609] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    20.609] (II) intel(0): Gamma: 2.20
[    20.609] (II) intel(0): No DPMS capabilities specified
[    20.609] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.609] (II) intel(0): First detailed timing is preferred mode
[    20.609] (II) intel(0): redX: 0.594 redY: 0.349   greenX: 0.325 greenY: 0.543
[    20.609] (II) intel(0): blueX: 0.157 blueY: 0.139   whiteX: 0.313 whiteY: 0.329
[    20.609] (II) intel(0): Manufacturer's mask: 0
[    20.609] (II) intel(0): Supported detailed timing:
[    20.609] (II) intel(0): clock: 69.3 MHz   Image Size:  331 x 207 mm
[    20.609] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1352 h_blank_end 1416 h_border: 0
[    20.609] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[    20.609] (II) intel(0):  LGPhilipsLCD
[    20.609] (II) intel(0): Monitor name: LP154WX4-TLAB
[    20.609] (II) intel(0): EDID (in hex):
[    20.609] (II) intel(0):     00ffffffffffff00320c013d00000000
[    20.609] (II) intel(0):     00120103802115780a14659859538b28
[    20.609] (II) intel(0):     23505400000001010101010101010101
[    20.609] (II) intel(0):     010101010101121b0088502010303018
[    20.609] (II) intel(0):     36004bcf100000190000000000000000
[    20.609] (II) intel(0):     00000000000000000000000000fe004c
[    20.609] (II) intel(0):     475068696c6970734c43440a000000fc
[    20.609] (II) intel(0):     004c503135345758342d544c41420023
[    20.609] (II) intel(0): EDID vendor "LPL", prod id 15617
[    20.609] (II) intel(0): Printing DDC gathered Modelines:
[    20.609] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    20.609] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    20.609] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    20.609] (II) intel(0): Printing probed modes for output LVDS1
[    20.610] (II) intel(0): Modeline "1280x800"x60.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    20.610] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.610] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.610] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.610] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.632] (II) intel(0): EDID for output VGA1
[    20.636] (II) intel(0): EDID for output HDMI1
[    20.636] (II) intel(0): EDID for output DP1
[    20.684] (II) intel(0): EDID for output DP2
[    20.981] (II) intel(0): EDID for output TV1
[    20.981] (II) intel(0): Output LVDS1 connected
[    20.981] (II) intel(0): Output VGA1 disconnected
[    20.981] (II) intel(0): Output HDMI1 disconnected
[    20.981] (II) intel(0): Output DP1 disconnected
[    20.981] (II) intel(0): Output DP2 disconnected
[    20.981] (II) intel(0): Output TV1 disconnected
[    20.981] (II) intel(0): Using exact sizes for initial modes
[    20.981] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    20.981] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.981] (II) intel(0): Kernel page flipping support detected, enabling
[    20.981] (**) intel(0): Display dimensions: (330, 210) mm
[    20.981] (**) intel(0): DPI set to (98, 96)
[    20.981] (II) Loading sub module "fb"
[    20.981] (II) LoadModule: "fb"
[    20.981] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.981] (II) Module fb: vendor="X.Org Foundation"
[    20.981]     compiled for 1.11.3, module version = 1.0.0
[    20.981]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.981] (II) Loading sub module "dri2"
[    20.981] (II) LoadModule: "dri2"
[    20.981] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.982] (II) Module dri2: vendor="X.Org Foundation"
[    20.982]     compiled for 1.11.3, module version = 1.2.0
[    20.982]     ABI class: X.Org Server Extension, version 6.0
[    20.982] (II) UnloadModule: "vesa"
[    20.982] (II) Unloading vesa
[    20.982] (II) UnloadModule: "fbdev"
[    20.982] (II) Unloading fbdev
[    20.982] (II) UnloadModule: "fbdevhw"
[    20.982] (II) Unloading fbdevhw
[    20.982] (==) Depth 24 pixmap format is 32 bpp
[    20.982] (II) intel(0): [DRI2] Setup complete
[    20.982] (II) intel(0): [DRI2]   DRI driver: i965
[    20.982] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    20.993] (II) UXA(0): Driver registered support for the following operations:
[    20.993] (II)         solid
[    20.993] (II)         copy
[    20.993] (II)         composite (RENDER acceleration)
[    20.993] (II)         put_image
[    20.993] (II)         get_image
[    20.993] (==) intel(0): Backing store disabled
[    20.993] (==) intel(0): Silken mouse enabled
[    20.993] (II) intel(0): Initializing HW Cursor
[    21.008] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.009] (==) intel(0): DPMS enabled
[    21.009] (==) intel(0): Intel XvMC decoder enabled
[    21.009] (II) intel(0): Set up textured video
[    21.009] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    21.009] (II) intel(0): direct rendering: DRI2 Enabled
[    21.009] (==) intel(0): hotplug detection: "enabled"
[    21.009] (--) RandR disabled
[    21.009] (II) Initializing built-in extension Generic Event Extension
[    21.009] (II) Initializing built-in extension SHAPE
[    21.009] (II) Initializing built-in extension MIT-SHM
[    21.009] (II) Initializing built-in extension XInputExtension
[    21.009] (II) Initializing built-in extension XTEST
[    21.009] (II) Initializing built-in extension BIG-REQUESTS
[    21.009] (II) Initializing built-in extension SYNC
[    21.009] (II) Initializing built-in extension XKEYBOARD
[    21.009] (II) Initializing built-in extension XC-MISC
[    21.009] (II) Initializing built-in extension SECURITY
[    21.009] (II) Initializing built-in extension XINERAMA
[    21.009] (II) Initializing built-in extension XFIXES
[    21.009] (II) Initializing built-in extension RENDER
[    21.009] (II) Initializing built-in extension RANDR
[    21.009] (II) Initializing built-in extension COMPOSITE
[    21.009] (II) Initializing built-in extension DAMAGE
[    21.022] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.022] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.022] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.022] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.022] (II) AIGLX: Loaded and initialized i965
[    21.022] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.022] (II) intel(0): Setting screen physical size to 338 x 211
[    21.031] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.035] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    21.035] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.035] (II) LoadModule: "evdev"
[    21.035] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.035] (II) Module evdev: vendor="X.Org Foundation"
[    21.035]     compiled for 1.11.3, module version = 2.7.0
[    21.035]     Module class: X.Org XInput Driver
[    21.035]     ABI class: X.Org XInput driver, version 16.0
[    21.035] (II) Using input driver 'evdev' for 'Power Button'
[    21.035] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.035] (**) Power Button: always reports core events
[    21.035] (**) evdev: Power Button: Device: "/dev/input/event2"
[    21.035] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.035] (--) evdev: Power Button: Found keys
[    21.035] (II) evdev: Power Button: Configuring as keyboard
[    21.035] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    21.035] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.035] (**) Option "xkb_rules" "evdev"
[    21.035] (**) Option "xkb_model" "pc105"
[    21.035] (**) Option "xkb_layout" "gb"
[    21.038] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    21.039] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    21.039] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.039] (II) Using input driver 'evdev' for 'Video Bus'
[    21.039] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.039] (**) Video Bus: always reports core events
[    21.039] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    21.039] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.039] (--) evdev: Video Bus: Found keys
[    21.039] (II) evdev: Video Bus: Configuring as keyboard
[    21.039] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8/event8"
[    21.039] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.039] (**) Option "xkb_rules" "evdev"
[    21.039] (**) Option "xkb_model" "pc105"
[    21.039] (**) Option "xkb_layout" "gb"
[    21.040] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    21.040] (II) No input driver specified, ignoring this device.
[    21.040] (II) This device may have been added with another device file.
[    21.040] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    21.040] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.040] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.040] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.040] (**) Sleep Button: always reports core events
[    21.040] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    21.040] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    21.040] (--) evdev: Sleep Button: Found keys
[    21.040] (II) evdev: Sleep Button: Configuring as keyboard
[    21.040] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    21.040] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    21.040] (**) Option "xkb_rules" "evdev"
[    21.040] (**) Option "xkb_model" "pc105"
[    21.040] (**) Option "xkb_layout" "gb"
[    21.041] (II) config/udev: Adding input device CKF7037 (/dev/input/event4)
[    21.041] (**) CKF7037: Applying InputClass "evdev keyboard catchall"
[    21.041] (II) Using input driver 'evdev' for 'CKF7037'
[    21.041] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.041] (**) CKF7037: always reports core events
[    21.041] (**) evdev: CKF7037: Device: "/dev/input/event4"
[    21.041] (--) evdev: CKF7037: Vendor 0x4f2 Product 0xb059
[    21.041] (--) evdev: CKF7037: Found keys
[    21.041] (II) evdev: CKF7037: Configuring as keyboard
[    21.041] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input4/event4"
[    21.041] (II) XINPUT: Adding extended input device "CKF7037" (type: KEYBOARD, id 9)
[    21.041] (**) Option "xkb_rules" "evdev"
[    21.041] (**) Option "xkb_model" "pc105"
[    21.041] (**) Option "xkb_layout" "gb"
[    21.042] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    21.042] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.042] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.042] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.042] (**) AT Translated Set 2 keyboard: always reports core events
[    21.042] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    21.042] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.042] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.042] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.042] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    21.042] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    21.042] (**) Option "xkb_rules" "evdev"
[    21.042] (**) Option "xkb_model" "pc105"
[    21.042] (**) Option "xkb_layout" "gb"
[    21.042] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    21.042] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.042] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.042] (II) LoadModule: "synaptics"
[    21.043] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.043] (II) Module synaptics: vendor="X.Org Foundation"
[    21.043]     compiled for 1.11.3, module version = 1.6.2
[    21.043]     Module class: X.Org XInput Driver
[    21.043]     ABI class: X.Org XInput driver, version 16.0
[    21.043] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    21.043] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.043] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.043] (**) Option "Device" "/dev/input/event7"
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5560
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4778
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    21.048] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.048] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.056] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    21.056] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    21.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.056] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    21.056] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    21.056] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.056] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.056] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    21.056] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.057] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[    21.057] (II) No input driver specified, ignoring this device.
[    21.057] (II) This device may have been added with another device file.
[    21.057] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    21.057] (II) No input driver specified, ignoring this device.
[    21.057] (II) This device may have been added with another device file.
[    21.059] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    21.059] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    21.059] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    21.059] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.059] (**) HP WMI hotkeys: always reports core events
[    21.059] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event6"
[    21.059] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    21.059] (--) evdev: HP WMI hotkeys: Found keys
[    21.059] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    21.059] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    21.059] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    21.059] (**) Option "xkb_rules" "evdev"
[    21.059] (**) Option "xkb_model" "pc105"
[    21.059] (**) Option "xkb_layout" "gb"
[    21.875] (II) intel(0): EDID vendor "LPL", prod id 15617
[    21.875] (II) intel(0): Printing DDC gathered Modelines:
[    21.875] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    23.869] (II) intel(0): EDID vendor "LPL", prod id 15617
[    23.869] (II) intel(0): Printing DDC gathered Modelines:
[    23.869] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    26.368] (II) XKB: reuse xkmfile /var/lib/xkb/server-3049F50FE3AF8D64C1AD99AA6BC01B68E61560BC.xkm
[    31.144] (II) intel(0): EDID vendor "LPL", prod id 15617
[    31.144] (II) intel(0): Printing DDC gathered Modelines:
[    31.144] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    43.988] (II) intel(0): EDID vendor "LPL", prod id 15617
[    43.988] (II) intel(0): Printing DDC gathered Modelines:
[    43.988] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)
[    48.085] (II) intel(0): EDID vendor "LPL", prod id 15617
[    48.085] (II) intel(0): Printing DDC gathered Modelines:
[    48.085] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1328 1352 1416  800 803 809 816 -hsync -vsync (48.9 kHz)

```

---

### Post by NikTh on 2012-10-16
Please **attach** the files , do not copy - paste them.. 

OR 

put the results between the brackets **[noparse]```
here
```[/noparse]** so can be readable.. 

edit your post please

**I edited my previous post.. see again the commands **
Thanks

---

### Post by NikTh on 2012-10-16
Here is a similar problem with yours. See how this user solved it. [http://ubuntuforums.org/showthread.php?t=1752444](http://ubuntuforums.org/showthread.php?t=1752444)

Thanks

---

### Post by cortman on 2012-10-16
Did the USB ports work previously?
Googling around reveals several bugs filed on this issue, but no resolutions that I can see. One user's problem was fixed after a reboot.

---

### Post by Sagitta12 on 2012-10-16
Yes, all USB ports worked for years, on 12.04 and on previous versions. I think I've read all that comes up with Google about this as well.... and tried quite a few different things. All USB's stopped from one day to the next, no warning, nothing been installed. At first I thought Compiz might have to do something with it, so I removed that, but that's about it. (I use the USB for printer, charge my phone, wireless mouse and downloads from a camera - usually only 1 thing plugged in at the time).

---

### Post by Sagitta12 on 2012-10-17
I got finally a backup of my files made through the network, onto another laptop. In preparation to install a whole new version of Ubuntu I did reset the settings in BIOS to factory default, not sure why , I just did - and this made the 4 USB ports active again. The old Ubuntu still works fine. 
I have never changed anything in BIOS myself, not even had a look at it, so not clear what caused this sudden malfunctioning of all USB ports.
Anyway happy camper now!
Thanks for all your help and efforts guys!

---

### Post by cortman on 2012-10-17
Glad that fixed it! No USB ports is a rather bad situation to be in.
Thanks also for posting back with your solution. Mark the thread [SOLVED] if you would, using the thread tools in the upper right.
Good luck!

---

### Post by Seamus83 on 2012-10-30
While I read over the "don't do this" comments. I want to thank you personally, because, as you were about to do, I was preparing to format and completely reload this computer until I read your post. Using your method solved the problem in five minutes and saved me a multitude of irritation (Especially since my backup hard drive wouldn't connect due to the fact that it as well is a USB device." Thanks a ton!!!

---

