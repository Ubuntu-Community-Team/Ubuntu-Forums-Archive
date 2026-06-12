---
title: "intel MCP limit exceeded?"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by nickjames1 on 2012-10-06
my computer occasionally randomly shutdown down. It happens especially while watching video on youtube or just a video through vlc.
It nmever did this before and even does it on windows ( I dual boot windows and 11.04)
The only clue I have is that, suddenly, the fan will start spinning really hard, becoming quite audible for 4 seconds and then it's off. I see this in the kernel logs
```
10/07/12 08:07:13 AM	a-W	kernel	[  692.659413] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36530, limit 35000
10/07/12 08:08:38 AM	a-W	kernel	[  777.490478] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36475, limit 35000
10/07/12 08:08:43 AM	a-W	kernel	[  782.480538] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40585, limit 35000
10/07/12 08:08:48 AM	a-W	kernel	[  787.472096] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39956, limit 35000
10/07/12 08:09:13 AM	a-W	kernel	[  812.420901] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37019, limit 35000
10/07/12 08:10:33 AM	a-W	kernel	[  892.261916] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37759, limit 35000
10/07/12 08:10:38 AM	a-W	kernel	[  897.251950] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37035, limit 35000
10/07/12 08:10:43 AM	a-W	kernel	[  902.241994] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38087, limit 35000
10/07/12 08:10:48 AM	a-W	kernel	[  907.232071] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37538, limit 35000
10/07/12 08:10:53 AM	a-W	kernel	[  912.222121] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38219, limit 35000
10/07/12 08:10:58 AM	a-W	kernel	[  917.212242] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38147, limit 35000
10/07/12 08:11:03 AM	a-W	kernel	[  922.202266] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37285, limit 35000
10/07/12 08:11:08 AM	a-W	kernel	[  927.192334] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40021, limit 35000
10/07/12 08:11:13 AM	a-W	kernel	[  932.182424] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40202, limit 35000
10/07/12 08:11:18 AM	a-W	kernel	[  937.172472] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38443, limit 35000
10/07/12 08:11:23 AM	a-W	kernel	[  942.162516] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38348, limit 35000
10/07/12 08:11:28 AM	a-W	kernel	[  947.152567] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38279, limit 35000
10/07/12 08:11:33 AM	a-W	kernel	[  952.142643] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36323, limit 35000
10/07/12 08:11:38 AM	a-W	kernel	[  957.132697] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38864, limit 35000
10/07/12 08:11:43 AM	a-W	kernel	[  962.122788] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37242, limit 35000
10/07/12 08:11:48 AM	a-W	kernel	[  967.112847] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39738, limit 35000
10/07/12 08:11:53 AM	a-W	kernel	[  972.102864] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39040, limit 35000
10/07/12 08:11:58 AM	a-W	kernel	[  977.092976] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39914, limit 35000
10/07/12 08:12:03 AM	a-W	kernel	[  982.082996] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 41278, limit 35000
10/07/12 08:12:08 AM	a-W	kernel	[  987.073069] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40302, limit 35000
10/07/12 08:12:13 AM	a-W	kernel	[  992.063291] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40096, limit 35000
10/07/12 08:12:18 AM	a-W	kernel	[  997.053267] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39923, limit 35000
10/07/12 08:12:23 AM	a-W	kernel	[ 1002.043314] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38243, limit 35000
10/07/12 08:12:28 AM	a-W	kernel	[ 1007.033363] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36768, limit 35000
10/07/12 08:12:33 AM	a-W	kernel	[ 1012.023404] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37944, limit 35000
10/07/12 08:12:38 AM	a-W	kernel	[ 1017.013475] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37773, limit 35000
10/07/12 08:12:43 AM	a-W	kernel	[ 1022.003478] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38868, limit 35000
10/07/12 08:12:48 AM	a-W	kernel	[ 1026.993532] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39847, limit 35000
10/07/12 08:12:53 AM	a-W	kernel	[ 1031.983617] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39293, limit 35000
10/07/12 08:12:58 AM	a-W	kernel	[ 1036.973708] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40070, limit 35000
10/07/12 08:13:03 AM	a-W	kernel	[ 1041.963751] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 41984, limit 35000
10/07/12 08:13:08 AM	a-W	kernel	[ 1046.953858] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39837, limit 35000
10/07/12 08:13:13 AM	a-W	kernel	[ 1051.943912] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40267, limit 35000
10/07/12 08:13:18 AM	a-W	kernel	[ 1056.933968] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40043, limit 35000
10/07/12 08:13:23 AM	a-W	kernel	[ 1061.924030] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39225, limit 35000
10/07/12 08:13:28 AM	a-W	kernel	[ 1066.914078] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38672, limit 35000
10/07/12 08:13:33 AM	a-W	kernel	[ 1071.904182] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38839, limit 35000
10/07/12 08:13:38 AM	a-W	kernel	[ 1076.894241] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38909, limit 35000
10/07/12 08:13:43 AM	a-W	kernel	[ 1081.884363] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39549, limit 35000
10/07/12 08:13:48 AM	a-W	kernel	[ 1086.874348] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40232, limit 35000
10/07/12 08:13:53 AM	a-W	kernel	[ 1091.864429] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40009, limit 35000
10/07/12 08:13:58 AM	a-W	kernel	[ 1096.854500] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37441, limit 35000
10/07/12 08:14:03 AM	a-W	kernel	[ 1101.844611] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36472, limit 35000
10/07/12 08:14:08 AM	a-W	kernel	[ 1106.834590] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36316, limit 35000
10/07/12 08:14:13 AM	a-W	kernel	[ 1111.824602] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39024, limit 35000
10/07/12 08:14:18 AM	a-W	kernel	[ 1116.814686] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37947, limit 35000
10/07/12 08:14:23 AM	a-W	kernel	[ 1121.804783] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36282, limit 35000
10/07/12 08:14:28 AM	a-W	kernel	[ 1126.794815] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40414, limit 35000
10/07/12 08:14:33 AM	a-W	kernel	[ 1131.784914] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38417, limit 35000
10/07/12 08:14:38 AM	a-W	kernel	[ 1136.774927] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 41038, limit 35000
10/07/12 08:14:43 AM	a-W	kernel	[ 1141.765010] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36479, limit 35000
10/07/12 08:14:48 AM	a-W	kernel	[ 1146.755722] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37943, limit 35000
10/07/12 08:14:53 AM	a-W	kernel	[ 1151.745105] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38705, limit 35000
10/07/12 08:14:58 AM	a-W	kernel	[ 1156.735189] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39957, limit 35000
10/07/12 08:15:03 AM	a-W	kernel	[ 1161.725237] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40298, limit 35000
10/07/12 08:15:08 AM	a-W	kernel	[ 1166.715355] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36444, limit 35000
10/07/12 08:15:13 AM	a-W	kernel	[ 1171.705392] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37268, limit 35000
10/07/12 08:15:18 AM	a-W	kernel	[ 1176.695427] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39513, limit 35000
10/07/12 08:15:23 AM	a-W	kernel	[ 1181.685494] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38599, limit 35000
10/07/12 08:15:28 AM	a-W	kernel	[ 1186.675560] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39991, limit 35000
10/07/12 08:15:33 AM	a-W	kernel	[ 1191.665645] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37375, limit 35000
10/07/12 08:15:38 AM	a-W	kernel	[ 1196.655681] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40926, limit 35000
10/07/12 08:15:43 AM	a-W	kernel	[ 1201.646671] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40045, limit 35000
10/07/12 08:15:48 AM	a-W	kernel	[ 1206.635810] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39077, limit 35000
10/07/12 08:15:53 AM	a-W	kernel	[ 1211.625879] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39078, limit 35000
10/07/12 08:15:58 AM	a-W	kernel	[ 1216.615964] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38790, limit 35000
10/07/12 08:16:03 AM	a-W	kernel	[ 1221.605991] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39152, limit 35000
10/07/12 08:16:08 AM	a-W	kernel	[ 1226.596090] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37243, limit 35000
10/07/12 08:16:13 AM	a-W	kernel	[ 1231.586123] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38990, limit 35000
10/07/12 08:16:18 AM	a-W	kernel	[ 1236.576229] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37765, limit 35000
10/07/12 08:16:23 AM	a-W	kernel	[ 1241.566297] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36333, limit 35000
10/07/12 08:16:28 AM	a-W	kernel	[ 1246.556387] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37171, limit 35000
10/07/12 08:16:33 AM	a-W	kernel	[ 1251.546417] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36256, limit 35000
10/07/12 08:16:38 AM	a-W	kernel	[ 1256.536440] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39357, limit 35000
10/07/12 08:16:43 AM	a-W	kernel	[ 1261.526502] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37462, limit 35000
10/07/12 08:16:48 AM	a-W	kernel	[ 1266.516565] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38383, limit 35000
10/07/12 08:16:53 AM	a-W	kernel	[ 1271.506636] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37421, limit 35000
10/07/12 08:16:58 AM	a-W	kernel	[ 1276.496721] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36765, limit 35000
10/07/12 08:17:03 AM	a-W	kernel	[ 1281.486746] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37282, limit 35000
10/07/12 08:17:08 AM	a-W	kernel	[ 1286.476849] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36871, limit 35000
10/07/12 08:17:13 AM	a-W	kernel	[ 1291.466860] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40108, limit 35000
10/07/12 08:17:18 AM	a-W	kernel	[ 1296.456992] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39817, limit 35000
10/07/12 08:17:23 AM	a-W	kernel	[ 1301.447030] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37021, limit 35000
10/07/12 08:17:28 AM	a-W	kernel	[ 1306.437088] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36232, limit 35000
10/07/12 08:17:33 AM	a-W	kernel	[ 1311.427134] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39703, limit 35000
10/07/12 08:17:38 AM	a-W	kernel	[ 1316.417211] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37794, limit 35000
10/07/12 08:17:43 AM	a-W	kernel	[ 1321.407247] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39905, limit 35000
10/07/12 08:17:48 AM	a-W	kernel	[ 1326.397327] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39383, limit 35000
10/07/12 08:17:53 AM	a-W	kernel	[ 1331.387408] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 41147, limit 35000
10/07/12 08:17:58 AM	a-W	kernel	[ 1336.377451] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40850, limit 35000
10/07/12 08:18:03 AM	a-W	kernel	[ 1341.367486] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38792, limit 35000
10/07/12 08:18:08 AM	a-W	kernel	[ 1346.357582] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 40336, limit 35000
10/07/12 08:18:13 AM	a-W	kernel	[ 1351.347626] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37559, limit 35000
10/07/12 08:18:18 AM	a-W	kernel	[ 1356.337744] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38719, limit 35000
10/07/12 08:18:23 AM	a-W	kernel	[ 1361.327773] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38462, limit 35000
10/07/12 08:18:28 AM	a-W	kernel	[ 1366.317871] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38531, limit 35000
10/07/12 08:18:33 AM	a-W	kernel	[ 1371.307941] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37327, limit 35000
10/07/12 08:18:38 AM	a-W	kernel	[ 1376.298007] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 36951, limit 35000
10/07/12 08:18:43 AM	a-W	kernel	[ 1381.287970] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37167, limit 35000
10/07/12 08:18:48 AM	a-W	kernel	[ 1386.278032] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 37553, limit 35000
10/07/12 08:18:53 AM	a-W	kernel	[ 1391.268160] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39126, limit 35000
10/07/12 08:18:58 AM	a-W	kernel	[ 1396.258176] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38313, limit 35000
10/07/12 08:19:03 AM	a-W	kernel	[ 1401.248272] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 38145, limit 35000
10/07/12 08:19:08 AM	a-W	kernel	[ 1406.238327] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39206, limit 35000
10/07/12 08:19:13 AM	a-W	kernel	[ 1411.228372] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39184, limit 35000
10/07/12 08:19:18 AM	a-W	kernel	[ 1416.218486] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 39479, limit 35000
```

---

### Post by lisati on 2012-10-06
It could be related to this report at launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045)

---

### Post by nickjames1 on 2012-10-07
I just checked on windows and confirmed that it does indeed happen on windows as well. It shuts down with the same sudden whirring up of fans. This may actually be a hardware problem. Would not be surprising since I spilled a whole glass of coffee on this laptop once, though quite long ago, and the keyboard has been sporadically working since then and just isn't responding correctly now.
I hadn't mentioned this before to see if I could get a response more enlightening than "it was the coffee"

---

### Post by cryptotheslow on 2012-10-07
I'd suspect it is overheating and automatically shutting down to protect itself from damage.

If you are nifty with the screwdrivers and have the patience of a saint you can disassemble the laptop and clean everything up inside with electrical contact cleaner. Pay particular attention to where the ribbon from the keyboard connects to the main board, as well as giving the mechanics of the keyboard a good blast with cleaner to try to remove any residual coffee gunk. Whilst in there it would be worthwhile removing, cleaning and reseating the cpu heatsink with a little blob of fresh thermal paste.

It's not difficult to do, just really fiddly with lots of tiny clips that like to break when you so much as look at them. Take your time and don't force anything - if it seems to require force you've probably missed a clip or hidden screw somewhere.

Good luck :D

---

