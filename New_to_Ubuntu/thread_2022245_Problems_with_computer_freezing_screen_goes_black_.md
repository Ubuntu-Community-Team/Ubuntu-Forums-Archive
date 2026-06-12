---
title: "Problems with computer freezing screen goes black then various error messages"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by htbw on 2012-07-10
My computer randomly freezes on me. I have been hunting around to see what could have caused it and I saw another post where someone had a freezing issue and one of the members suggested he try a certain string of text. Well, here is the result.. very long and I'm even more confused, although this one seems to imply an issue with the monitor. The error messages mention battery, then something about the memory???

The last time it happened, I was installing some software. I think I was going a little nuts and had about 4 installs running at the same time. There was a reference to Kernel failure or something like that. (Sorry for the vague terminology)

I'm hoping for some help before this issue continues to get worse and eventually causes the computer to become toast and require a reinstall of the OS (This has happened a few times already) Please please please help :)


                                  cat /proc/interrupts
dmesg
lspci -v
cat /var/log/Xorg.0.log 





[208615.473490]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208615.473491]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208615.473493]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208615.473496] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208615.473498] [drm:radeon_vga_detect] *ERROR* VGA-1: probed a monitor but no|invalid EDID  
 [208615.524619] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208615.524621] Raw EDID:  
 [208615.524622]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208615.524624]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208615.524625]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208615.524627]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208615.524628]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208615.524630]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208615.524631]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208615.524632]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208615.574094] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208615.574095] Raw EDID:  
 [208615.574097]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208615.574098]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208615.574100]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208615.574101]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208615.574103]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208615.574104]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208615.574106]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208615.574107]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208615.623564] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208615.623566] Raw EDID:  
 [208615.623567]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208615.623569]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208615.623570]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208615.623572]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208615.623573]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208615.623575]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208615.623576]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208615.623578]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208615.673020] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208615.673021] Raw EDID:  
 [208615.673022]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208615.673024]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208615.673025]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208615.673027]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208615.673028]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208615.673030]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208615.673031]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208615.673033]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208615.673035] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208730.954937] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208730.954941] Raw EDID:  
 [208730.954943]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208730.954945]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208730.954946]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208730.954947]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208730.954949]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208730.954950]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208730.954952]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208730.954953]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.004435] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.004437] Raw EDID:  
 [208731.004438]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.004440]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.004441]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.004442]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.004444]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.004445]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.004447]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.004448]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.053910] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.053912] Raw EDID:  
 [208731.053913]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.053914]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.053916]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.053917]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.053919]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.053920]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.053921]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.053923]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.103366] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.103367] Raw EDID:  
 [208731.103368]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.103370]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.103371]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.103373]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.103374]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.103376]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.103377]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.103378]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.103381] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208731.103383] [drm:radeon_vga_detect] *ERROR* VGA-1: probed a monitor but no|invalid EDID  
 [208731.154486] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.154488] Raw EDID:  
 [208731.154489]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.154490]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.154492]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.154493]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.154495]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.154496]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.154497]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.154499]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.203933] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.203934] Raw EDID:  
 [208731.203936]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.203937]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.203938]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.203940]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.203941]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.203943]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.203944]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.203946]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.253406] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.253407] Raw EDID:  
 [208731.253408]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.253410]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.253411]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.253413]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.253414]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.253416]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.253417]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.253418]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.302857] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208731.302858] Raw EDID:  
 [208731.302860]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208731.302861]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208731.302862]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208731.302864]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208731.302865]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208731.302867]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208731.302868]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208731.302870]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208731.302871] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208744.225047] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)  
 [208781.388119] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.388123] Raw EDID:  
 [208781.388126]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.388127]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.388129]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.388130]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.388132]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.388133]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.388134]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.388136]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.447325] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.447327] Raw EDID:  
 [208781.447328]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.447329]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.447331]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.447333]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.447334]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.447336]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.447337]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.447339]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.496857] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.496859] Raw EDID:  
 [208781.496860]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.496861]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.496863]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.496864]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.496866]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.496867]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.496869]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.496870]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.546302] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.546304] Raw EDID:  
 [208781.546305]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.546307]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.546308]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.546310]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.546311]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.546313]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.546314]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.546315]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.546319] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208781.546321] [drm:radeon_vga_detect] *ERROR* VGA-1: probed a monitor but no|invalid EDID  
 [208781.597422] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.597423] Raw EDID:  
 [208781.597425]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.597426]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.597428]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.597429]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.597431]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.597432]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.597434]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.597435]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.646863] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.646865] Raw EDID:  
 [208781.646866]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.646867]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.646869]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.646870]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.646872]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.646873]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.646875]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.646876]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.696317] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.696318] Raw EDID:  
 [208781.696320]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.696321]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.696323]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.696324]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.696326]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.696327]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.696328]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.696330]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.745760] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208781.745761] Raw EDID:  
 [208781.745763]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208781.745764]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208781.745766]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208781.745767]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208781.745769]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208781.745770]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208781.745771]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208781.745773]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208781.745775] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208838.023404] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.023407] Raw EDID:  
 [208838.023410]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.023411]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.023413]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.023414]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.023415]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.023417]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.023418]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.023420]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.072930] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.072932] Raw EDID:  
 [208838.072933]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.072934]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.072936]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.072937]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.072939]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.072940]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.072942]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.072943]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.122489] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.122491] Raw EDID:  
 [208838.122492]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.122493]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.122495]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.122496]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.122498]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.122499]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.122501]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.122502]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.171951] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.171952] Raw EDID:  
 [208838.171953]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.171955]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.171956]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.171958]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.171959]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.171961]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.171962]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.171964]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.171967] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 [208838.171969] [drm:radeon_vga_detect] *ERROR* VGA-1: probed a monitor but no|invalid EDID  
 [208838.223073] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.223075] Raw EDID:  
 [208838.223076]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.223078]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.223079]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.223080]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.223082]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.223083]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.223085]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.223086]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.272528] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.272529] Raw EDID:  
 [208838.272530]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.272532]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.272533]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.272535]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.272536]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.272538]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.272539]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.272541]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.321971] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.321973] Raw EDID:  
 [208838.321974]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.321976]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.321977]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.321978]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.321980]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.321981]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.321983]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.321984]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.371417] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 173  
 [208838.371418] Raw EDID:  
 [208838.371419]      00 ff ff ff ff ff ff 00 04 72 cc 01 4f 12 10 12  
 [208838.371421]      15 15 01 03 6c 29 17 78 ea ac 25 a5 55 48 9a 27  
 [208838.371422]      13 50 54 bf ee 00 81 c0 81 00 01 01 01 01 01 01  
 [208838.371424]      01 01 01 01 01 01 66 21 56 aa 51 00 1e 30 46 8f  
 [208838.371425]      33 00 9a e6 10 00 00 1e 00 00 00 fd 00 38 4b 1f  
 [208838.371427]      53 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  
 [208838.371428]      63 65 72 20 50 31 38 36 48 56 0a 20 00 00 00 ff  
 [208838.371429]      00 4c 50 5a 30 57 30 07 08 34 33 33 31 0a 00 27  
 [208838.371431] radeon 0000:01:05.0: VGA-1: EDID block 0 invalid.  
 twirpy@twirpy-GA-MA74GM-S2:~$ lspci -v  
 00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge  
     Subsystem: Giga-byte Technology Device 5000  
     Flags: bus master, 66MHz, medium devsel, latency 32  
     Kernel modules: ati-agp  
 

 00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])  
     Flags: bus master, 66MHz, medium devsel, latency 99  
     Bus: primary=00, secondary=01, subordinate=01, sec-latency=68  
     I/O behind bridge: 0000e000-0000efff  
     Memory behind bridge: fde00000-fdffffff  
     Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff  
     Capabilities: <access denied>  
     Kernel modules: shpchp  
 

 00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])  
     Flags: bus master, fast devsel, latency 0  
     Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
     I/O behind bridge: 0000d000-0000dfff  
     Memory behind bridge: fdd00000-fddfffff  
     Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff  
     Capabilities: <access denied>  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])  
     Subsystem: Giga-byte Technology GA-MA770-DS3rev2.0 Motherboard  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22  
     I/O ports at ff00 [size=8]  
     I/O ports at fe00 [size=4]  
     I/O ports at fd00 [size=8]  
     I/O ports at fc00 [size=4]  
     I/O ports at fb00 [size=16]  
     Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: <access denied>  
     Kernel driver in use: ahci  
 

 00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16  
     Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16  
     Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17  
     Memory at fe02c000 (32-bit, non-prefetchable) [size=256]  
     Capabilities: <access denied>  
     Kernel driver in use: ehci_hcd  
 

 00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18  
     Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18  
     Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19  
     Memory at fe029000 (32-bit, non-prefetchable) [size=256]  
     Capabilities: <access denied>  
     Kernel driver in use: ehci_hcd  
 

 00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)  
     Subsystem: Giga-byte Technology GA-MA770-DS3rev2.0 Motherboard  
     Flags: 66MHz, medium devsel  
     Capabilities: <access denied>  
     Kernel driver in use: piix4_smbus  
     Kernel modules: sp5100_tco, i2c-piix4  
 

 00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [Master SecP PriP])  
     Subsystem: Giga-byte Technology Device 5002  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16  
     I/O ports at 01f0 [size=8]  
     I/O ports at 03f4 [size=1]  
     I/O ports at 0170 [size=8]  
     I/O ports at 0374 [size=1]  
     I/O ports at fa00 [size=16]  
     Capabilities: <access denied>  
     Kernel driver in use: pata_atiixp  
     Kernel modules: pata_atiixp  
 

 00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)  
     Subsystem: Giga-byte Technology Device a002  
     Flags: bus master, slow devsel, latency 32, IRQ 16  
     Memory at fe024000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: snd_hda_intel  
     Kernel modules: snd-hda-intel  
 

 00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller  
     Subsystem: Giga-byte Technology Device 5001  
     Flags: bus master, 66MHz, medium devsel, latency 0  
 

 00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])  
     Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64  
     Bus: primary=00, secondary=03, subordinate=03, sec-latency=64  
     I/O behind bridge: 0000c000-0000cfff  
     Memory behind bridge: fdc00000-fdcfffff  
     Prefetchable memory behind bridge: fdb00000-fdbfffff  
 

 00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])  
     Subsystem: Giga-byte Technology Device 5004  
     Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18  
     Memory at fe028000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration  
     Flags: fast devsel  
     Capabilities: <access denied>  
 

 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map  
     Flags: fast devsel  
 

 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller  
     Flags: fast devsel  
   
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control  
     Flags: fast devsel  
     Capabilities: <access denied>  
     Kernel modules: k10temp  
 

 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control  
     Flags: fast devsel  
 

 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon 2100 (prog-if 00 [VGA controller])  
     Subsystem: Giga-byte Technology Device d000  
     Flags: bus master, fast devsel, latency 32, IRQ 18  
     Memory at d8000000 (64-bit, prefetchable) [size=128M]  
     Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]  
     I/O ports at ee00 [size=256]  
     Memory at fde00000 (32-bit, non-prefetchable) [size=1M]  
     Expansion ROM at <unassigned> [disabled]  
     Capabilities: <access denied>  
     Kernel driver in use: radeon  
     Kernel modules: radeon  
 

 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)  
     Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard  
     Flags: bus master, fast devsel, latency 0, IRQ 40  
     I/O ports at de00 [size=256]  
     Memory at fdaff000 (64-bit, prefetchable) [size=4K]  
     Memory at fdae0000 (64-bit, prefetchable) [size=64K]  
     [virtual] Expansion ROM at fda00000 [disabled] [size=64K]  
     Capabilities: <access denied>  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
 

 twirpy@twirpy-GA-MA74GM-S2:~$ cat /var/log/Xorg.0.log

---

