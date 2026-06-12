---
title: "cross compiling libva-1.0.16"
date: 2012-08-16
forum: Programming Talk
---

### Post by active1 on 2012-08-16
hi, i'm trying to cross compile [libva-1.0.16]("http://cgit.freedesktop.org/libva/snapshot/libva-1.0.16.tar.gz")
i configured it successfully with:
```
 ./configure --host=i586-mingw32msvc --prefix=/usr/i586-mingw32msvc --disable-glx
```
but i have a problem with "make":
```
../../va/va.h:185: error: expected ')' before 'dpy'
../../va/va.h:190: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:199: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:212: error: expected ')' before 'dpy'
../../va/va.h:215: error: storage class specified for parameter 'VAPrivFunc'
../../va/va.h:221: error: expected declaration specifiers before 'VAPrivFunc'
../../va/va.h:243: error: storage class specified for parameter 'VAProfile'
../../va/va.h:257: error: storage class specified for parameter 'VAEntrypoint'
../../va/va.h:268: error: storage class specified for parameter 'VAConfigAttribType'
../../va/va.h:277: error: expected specifier-qualifier-list before 'VAConfigAttribType'
../../va/va.h:279: error: storage class specified for parameter 'VAConfigAttrib'
../../va/va.h:301: error: expected ')' before 'dpy'
../../va/va.h:306: error: expected ')' before 'dpy'
../../va/va.h:311: error: expected ')' before 'dpy'
../../va/va.h:320: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:332: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:347: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:356: error: storage class specified for parameter 'VAGenericID'
../../va/va.h:358: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VAConfigID'
../../va/va.h:365: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:377: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:390: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:416: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VAContextID'
../../va/va.h:418: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VASurfaceID'
../../va/va.h:432: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:450: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:469: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:485: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:498: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VABufferID'
../../va/va.h:525: error: storage class specified for parameter 'VABufferType'
../../va/va.h:533: error: storage class specified for parameter 'VAEncMiscParameterType'
../../va/va.h:554: error: expected specifier-qualifier-list before 'VAEncMiscParameterType'
../../va/va.h:556: error: storage class specified for parameter 'VAEncMiscParameterBuffer'
../../va/va.h:568: error: storage class specified for parameter 'VAEncMiscParameterRateControl'
../../va/va.h:573: error: storage class specified for parameter 'VAEncMiscParameterFrameRate'
../../va/va.h:583: error: storage class specified for parameter 'VAEncMiscParameterMaxSliceSize'
../../va/va.h:590: error: storage class specified for parameter 'VAEncMiscParameterAIR'
../../va/va.h:612: error: storage class specified for parameter 'VASliceParameterBufferBase'
../../va/va.h:624: error: storage class specified for parameter 'VAQMatrixBufferJPEG'
../../va/va.h:628: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:632: error: storage class specified for parameter 'VAEncPictureParameterBufferJPEG'
In file included from ../../va/va.h:634,
                 from dri1_util.c:10:
../../va/va_dec_jpeg.h:73: error: storage class specified for parameter 'VAPictureParameterBufferJPEGBaseline'
../../va/va_dec_jpeg.h:92: error: storage class specified for parameter 'VAIQMatrixBufferJPEGBaseline'
../../va/va_dec_jpeg.h:128: error: storage class specified for parameter 'VAHuffmanTableBufferJPEGBaseline'
../../va/va_dec_jpeg.h:168: error: storage class specified for parameter 'VASliceParameterBufferJPEGBaseline'
In file included from dri1_util.c:10:
../../va/va.h:649: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:672: error: storage class specified for parameter 'VAPictureParameterBufferMPEG2'
../../va/va.h:685: error: storage class specified for parameter 'VAIQMatrixBufferMPEG2'
../../va/va.h:698: error: storage class specified for parameter 'VASliceParameterBufferMPEG2'
../../va/va.h:737: error: storage class specified for parameter 'VAMacroblockParameterBufferMPEG2'
../../va/va.h:766: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:808: error: storage class specified for parameter 'VAPictureParameterBufferMPEG4'
../../va/va.h:817: error: storage class specified for parameter 'VAIQMatrixBufferMPEG4'
../../va/va.h:828: error: storage class specified for parameter 'VASliceParameterBufferMPEG4'
../../va/va.h:841: error: storage class specified for parameter 'VAMvModeVC1'
../../va/va.h:858: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:1000: error: storage class specified for parameter 'VAPictureParameterBufferVC1'
../../va/va.h:1028: error: storage class specified for parameter 'VASliceParameterBufferVC1'
../../va/va.h:1041: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:1046: error: storage class specified for parameter 'VAPictureH264'
../../va/va.h:1061: error: expected specifier-qualifier-list before 'VAPictureH264'
../../va/va.h:1107: error: storage class specified for parameter 'VAPictureParameterBufferH264'
../../va/va.h:1114: error: storage class specified for parameter 'VAIQMatrixBufferH264'
../../va/va.h:1154: error: expected specifier-qualifier-list before 'VAPictureH264'
../../va/va.h:1170: error: storage class specified for parameter 'VASliceParameterBufferH264'
../../va/va.h:1180: error: storage class specified for parameter 'VAEncPictureType'
../../va/va.h:1196: error: storage class specified for parameter 'VAEncSliceParameterBuffer'
../../va/va.h:1217: error: storage class specified for parameter 'VAEncSequenceParameterBufferH264'
../../va/va.h:1223: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:1229: error: storage class specified for parameter 'VAEncPictureParameterBufferH264'
../../va/va.h:1242: error: storage class specified for parameter 'VAEncSequenceParameterBufferH263'
../../va/va.h:1246: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:1252: error: storage class specified for parameter 'VAEncPictureParameterBufferH263'
../../va/va.h:1271: error: storage class specified for parameter 'VAEncSequenceParameterBufferMPEG4'
../../va/va.h:1275: error: expected specifier-qualifier-list before 'VASurfaceID'
../../va/va.h:1283: error: storage class specified for parameter 'VAEncPictureParameterBufferMPEG4'
../../va/va.h:1303: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1319: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1357: error: storage class specified for parameter 'VACodedBufferSegment'
../../va/va.h:1367: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1378: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1387: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1403: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1413: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1426: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1442: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1455: error: storage class specified for parameter 'VASurfaceStatus'
../../va/va.h:1460: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1470: error: storage class specified for parameter 'VADecodeErrorType'
../../va/va.h:1481: error: expected specifier-qualifier-list before 'VADecodeErrorType'
../../va/va.h:1482: error: storage class specified for parameter 'VASurfaceDecodeMBErrors'
../../va/va.h:1492: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1538: error: storage class specified for parameter 'VAImageFormat'
../../va/va.h:1540: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VAImageID'
../../va/va.h:1544: error: expected specifier-qualifier-list before 'VAImageID'
../../va/va.h:1581: error: storage class specified for parameter 'VAImage'
../../va/va.h:1585: error: expected ')' before 'dpy'
../../va/va.h:1594: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1607: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1618: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1623: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1638: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1654: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1699: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1712: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'VASubpictureID'
../../va/va.h:1716: error: expected ')' before 'dpy'
../../va/va.h:1735: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1745: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1754: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1763: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1778: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1791: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1804: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1827: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1840: error: storage class specified for parameter 'VARectangle'
../../va/va.h:1857: error: storage class specified for parameter 'VADisplayAttribBLEMode'
../../va/va.h:1953: error: storage class specified for parameter 'VADisplayAttribType'
../../va/va.h:1962: error: expected specifier-qualifier-list before 'VADisplayAttribType'
../../va/va.h:1968: error: storage class specified for parameter 'VADisplayAttribute'
../../va/va.h:1972: error: expected ')' before 'dpy'
../../va/va.h:1981: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:1993: error: expected declaration specifiers before 'VAStatus'
../../va/va.h:2005: error: expected declaration specifiers before 'VAStatus'
In file included from dri1_util.c:11:
../../va/va_backend.h:36:29: error: linux/videodev2.h: No such file or directory
In file included from dri1_util.c:11:
../../va/va_backend.h:38: error: storage class specified for parameter 'VADriverContextP'
../../va/va_backend.h:39: error: storage class specified for parameter 'VADisplayContextP'
../../va/va_backend.h:43: error: expected specifier-qualifier-list before 'VAStatus'
../../va/va_backend.h:380: warning: empty declaration
../../va/va_backend.h:438: warning: empty declaration
../../va/va_backend.h:445: error: expected specifier-qualifier-list before 'VADisplayContextP'
../../va/va_backend.h:462: warning: empty declaration
../../va/va_backend.h:464: error: expected declaration specifiers or '...' before '*' token
../../va/va_backend.h:465: error: expected ')' before 'driver_context'
In file included from dri1_util.c:13:
va_dri.h:67: error: storage class specified for parameter '__DRIid'
va_dri.h:68: error: storage class specified for parameter '__DRInativeDisplay'
va_dri.h:70: error: expected declaration specifiers before '_XFUNCPROTOBEGIN'
va_dri.h:80: error: expected declaration specifiers or '...' before 'drm_handle_t'
va_dri.h:83: error: expected declaration specifiers or '...' before 'drm_magic_t'
va_dri.h:92: error: expected declaration specifiers or '...' before 'XID'
va_dri.h:92: error: expected declaration specifiers or '...' before 'drm_context_t'
va_dri.h:95: error: expected declaration specifiers or '...' before 'XID'
va_dri.h:95: error: expected declaration specifiers or '...' before 'drm_context_t'
va_dri.h:97: error: expected ')' before '*' token
va_dri.h:100: error: expected ')' before '*' token
va_dri.h:103: error: expected ')' before '*' token
va_dri.h:106: error: expected declaration specifiers or '...' before 'Drawable'
va_dri.h:109: error: expected declaration specifiers or '...' before 'drm_clip_rect_t'
va_dri.h:111: error: expected declaration specifiers or '...' before 'drm_clip_rect_t'
va_dri.h:114: error: expected declaration specifiers or '...' before 'drm_handle_t'
va_dri.h:117: error: expected declaration specifiers before '_XFUNCPROTOEND'
In file included from va_dricommon.h:7,
                 from dri1_util.c:14:
/usr/include/libdrm/drm.h:47:24: error: sys/ioccom.h: No such file or directory
In file included from va_dricommon.h:7,
                 from dri1_util.c:14:
/usr/include/libdrm/drm.h:50: error: storage class specified for parameter '__u8'
/usr/include/libdrm/drm.h:51: error: storage class specified for parameter '__s16'
/usr/include/libdrm/drm.h:52: error: storage class specified for parameter '__u16'
/usr/include/libdrm/drm.h:53: error: storage class specified for parameter '__s32'
/usr/include/libdrm/drm.h:54: error: storage class specified for parameter '__u32'
/usr/include/libdrm/drm.h:55: error: storage class specified for parameter '__s64'
/usr/include/libdrm/drm.h:56: error: storage class specified for parameter '__u64'
/usr/include/libdrm/drm.h:57: error: storage class specified for parameter 'drm_handle_t'
/usr/include/libdrm/drm.h:72: error: storage class specified for parameter 'drm_context_t'
/usr/include/libdrm/drm.h:73: error: storage class specified for parameter 'drm_drawable_t'
/usr/include/libdrm/drm.h:74: error: storage class specified for parameter 'drm_magic_t'
/usr/include/libdrm/drm.h:90: warning: empty declaration
/usr/include/libdrm/drm.h:98: warning: empty declaration
/usr/include/libdrm/drm.h:109: warning: empty declaration
/usr/include/libdrm/drm.h:121: warning: empty declaration
/usr/include/libdrm/drm.h:138: warning: empty declaration
/usr/include/libdrm/drm.h:148: warning: empty declaration
/usr/include/libdrm/drm.h:153: warning: empty declaration
/usr/include/libdrm/drm.h:157: warning: empty declaration
/usr/include/libdrm/drm.h:172: warning: empty declaration
/usr/include/libdrm/drm.h:185: warning: empty declaration
/usr/include/libdrm/drm.h:199: warning: empty declaration
/usr/include/libdrm/drm.h:204: warning: empty declaration
/usr/include/libdrm/drm.h:221: warning: empty declaration
/usr/include/libdrm/drm.h:233: warning: empty declaration
/usr/include/libdrm/drm.h:253: warning: empty declaration
/usr/include/libdrm/drm.h:264: warning: empty declaration
/usr/include/libdrm/drm.h:279: warning: empty declaration
/usr/include/libdrm/drm.h:289: warning: empty declaration
/usr/include/libdrm/drm.h:318: warning: empty declaration
/usr/include/libdrm/drm.h:341: warning: empty declaration
/usr/include/libdrm/drm.h:349: warning: empty declaration
/usr/include/libdrm/drm.h:357: warning: empty declaration
/usr/include/libdrm/drm.h:369: warning: empty declaration
/usr/include/libdrm/drm.h:382: warning: empty declaration
/usr/include/libdrm/drm.h:402: warning: empty declaration
/usr/include/libdrm/drm.h:407: warning: empty declaration
/usr/include/libdrm/drm.h:415: error: expected specifier-qualifier-list before 'drm_context_t'
/usr/include/libdrm/drm.h:417: warning: empty declaration
/usr/include/libdrm/drm.h:425: warning: empty declaration
/usr/include/libdrm/drm.h:431: error: expected specifier-qualifier-list before 'drm_drawable_t'
/usr/include/libdrm/drm.h:432: warning: empty declaration
/usr/include/libdrm/drm.h:439: error: storage class specified for parameter 'drm_drawable_info_type_t'
/usr/include/libdrm/drm.h:442: error: expected specifier-qualifier-list before 'drm_drawable_t'
/usr/include/libdrm/drm.h:446: warning: empty declaration
/usr/include/libdrm/drm.h:452: error: expected specifier-qualifier-list before 'drm_magic_t'
/usr/include/libdrm/drm.h:453: warning: empty declaration
/usr/include/libdrm/drm.h:465: warning: empty declaration
/usr/include/libdrm/drm.h:475: warning: empty declaration
/usr/include/libdrm/drm.h:485: warning: empty declaration
/usr/include/libdrm/drm.h:492: warning: empty declaration
/usr/include/libdrm/drm.h:502: warning: empty declaration
/usr/include/libdrm/drm.h:513: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm.h:515: warning: empty declaration
/usr/include/libdrm/drm.h:524: warning: empty declaration
/usr/include/libdrm/drm.h:536: warning: empty declaration
/usr/include/libdrm/drm.h:546: warning: empty declaration
/usr/include/libdrm/drm.h:567: warning: empty declaration
/usr/include/libdrm/drm.h:575: warning: empty declaration
/usr/include/libdrm/drm.h:585: warning: empty declaration
/usr/include/libdrm/drm.h:590: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm.h:592: warning: empty declaration
/usr/include/libdrm/drm.h:597: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm.h:601: warning: empty declaration
/usr/include/libdrm/drm.h:606: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm.h:613: warning: empty declaration
/usr/include/libdrm/drm.h:617: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm.h:619: warning: empty declaration
In file included from /usr/include/libdrm/drm.h:621,
                 from va_dricommon.h:7,
                 from dri1_util.c:14:
/usr/include/libdrm/drm_mode.h:85: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:94: warning: empty declaration
/usr/include/libdrm/drm_mode.h:97: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:107: warning: empty declaration
/usr/include/libdrm/drm_mode.h:110: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:121: warning: empty declaration
/usr/include/libdrm/drm_mode.h:130: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:137: warning: empty declaration
/usr/include/libdrm/drm_mode.h:168: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:185: warning: empty declaration
/usr/include/libdrm/drm_mode.h:194: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:196: warning: empty declaration
/usr/include/libdrm/drm_mode.h:199: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:208: warning: empty declaration
/usr/include/libdrm/drm_mode.h:211: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm_mode.h:214: warning: empty declaration
/usr/include/libdrm/drm_mode.h:217: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:220: warning: empty declaration
/usr/include/libdrm/drm_mode.h:223: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:230: warning: empty declaration
/usr/include/libdrm/drm_mode.h:264: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:269: warning: empty declaration
/usr/include/libdrm/drm_mode.h:272: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:274: warning: empty declaration
/usr/include/libdrm/drm_mode.h:294: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:302: warning: empty declaration
/usr/include/libdrm/drm_mode.h:305: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:312: warning: empty declaration
/usr/include/libdrm/drm_mode.h:340: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:345: warning: empty declaration
/usr/include/libdrm/drm_mode.h:349: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:357: warning: empty declaration
/usr/include/libdrm/drm_mode.h:362: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:370: warning: empty declaration
/usr/include/libdrm/drm_mode.h:373: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm_mode.h:374: warning: empty declaration
In file included from va_dricommon.h:7,
                 from dri1_util.c:14:
/usr/include/libdrm/drm.h:741: error: expected specifier-qualifier-list before '__u32'
/usr/include/libdrm/drm.h:743: warning: empty declaration
/usr/include/libdrm/drm.h:750: error: expected specifier-qualifier-list before '__u64'
/usr/include/libdrm/drm.h:755: warning: empty declaration
/usr/include/libdrm/drm.h:761: error: storage class specified for parameter 'drm_clip_rect_t'
/usr/include/libdrm/drm.h:762: error: storage class specified for parameter 'drm_drawable_info_t'
/usr/include/libdrm/drm.h:763: error: storage class specified for parameter 'drm_tex_region_t'
/usr/include/libdrm/drm.h:764: error: storage class specified for parameter 'drm_hw_lock_t'
/usr/include/libdrm/drm.h:765: error: storage class specified for parameter 'drm_version_t'
/usr/include/libdrm/drm.h:766: error: storage class specified for parameter 'drm_unique_t'
/usr/include/libdrm/drm.h:767: error: storage class specified for parameter 'drm_list_t'
/usr/include/libdrm/drm.h:768: error: storage class specified for parameter 'drm_block_t'
/usr/include/libdrm/drm.h:769: error: storage class specified for parameter 'drm_control_t'
/usr/include/libdrm/drm.h:770: error: storage class specified for parameter 'drm_map_type_t'
/usr/include/libdrm/drm.h:771: error: storage class specified for parameter 'drm_map_flags_t'
/usr/include/libdrm/drm.h:772: error: storage class specified for parameter 'drm_ctx_priv_map_t'
/usr/include/libdrm/drm.h:773: error: storage class specified for parameter 'drm_map_t'
/usr/include/libdrm/drm.h:774: error: storage class specified for parameter 'drm_client_t'
/usr/include/libdrm/drm.h:775: error: storage class specified for parameter 'drm_stat_type_t'
/usr/include/libdrm/drm.h:776: error: storage class specified for parameter 'drm_stats_t'
/usr/include/libdrm/drm.h:777: error: storage class specified for parameter 'drm_lock_flags_t'
/usr/include/libdrm/drm.h:778: error: storage class specified for parameter 'drm_lock_t'
/usr/include/libdrm/drm.h:779: error: storage class specified for parameter 'drm_dma_flags_t'
/usr/include/libdrm/drm.h:780: error: storage class specified for parameter 'drm_buf_desc_t'
/usr/include/libdrm/drm.h:781: error: storage class specified for parameter 'drm_buf_info_t'
/usr/include/libdrm/drm.h:782: error: storage class specified for parameter 'drm_buf_free_t'
/usr/include/libdrm/drm.h:783: error: storage class specified for parameter 'drm_buf_pub_t'
/usr/include/libdrm/drm.h:784: error: storage class specified for parameter 'drm_buf_map_t'
/usr/include/libdrm/drm.h:785: error: storage class specified for parameter 'drm_dma_t'
/usr/include/libdrm/drm.h:786: error: storage class specified for parameter 'drm_wait_vblank_t'
/usr/include/libdrm/drm.h:787: error: storage class specified for parameter 'drm_agp_mode_t'
/usr/include/libdrm/drm.h:788: error: storage class specified for parameter 'drm_ctx_flags_t'
/usr/include/libdrm/drm.h:789: error: storage class specified for parameter 'drm_ctx_t'
/usr/include/libdrm/drm.h:790: error: storage class specified for parameter 'drm_ctx_res_t'
/usr/include/libdrm/drm.h:791: error: storage class specified for parameter 'drm_draw_t'
/usr/include/libdrm/drm.h:792: error: storage class specified for parameter 'drm_update_draw_t'
/usr/include/libdrm/drm.h:793: error: storage class specified for parameter 'drm_auth_t'
/usr/include/libdrm/drm.h:794: error: storage class specified for parameter 'drm_irq_busid_t'
/usr/include/libdrm/drm.h:795: error: storage class specified for parameter 'drm_vblank_seq_type_t'
/usr/include/libdrm/drm.h:797: error: storage class specified for parameter 'drm_agp_buffer_t'
/usr/include/libdrm/drm.h:798: error: storage class specified for parameter 'drm_agp_binding_t'
/usr/include/libdrm/drm.h:799: error: storage class specified for parameter 'drm_agp_info_t'
/usr/include/libdrm/drm.h:800: error: storage class specified for parameter 'drm_scatter_gather_t'
/usr/include/libdrm/drm.h:801: error: storage class specified for parameter 'drm_set_version_t'
In file included from va_dricommon.h:8,
                 from dri1_util.c:14:
/usr/include/libdrm/drm_sarea.h:56: warning: empty declaration
/usr/include/libdrm/drm_sarea.h:65: warning: empty declaration
/usr/include/libdrm/drm_sarea.h:75: error: expected specifier-qualifier-list before 'drm_context_t'
/usr/include/libdrm/drm_sarea.h:76: warning: empty declaration
/usr/include/libdrm/drm_sarea.h:78: error: storage class specified for parameter 'drm_sarea_drawable_t'
/usr/include/libdrm/drm_sarea.h:79: error: storage class specified for parameter 'drm_sarea_frame_t'
/usr/include/libdrm/drm_sarea.h:80: error: storage class specified for parameter 'drm_sarea_t'
In file included from dri1_util.c:14:
va_dricommon.h:24: warning: empty declaration
va_dricommon.h:38: warning: empty declaration
va_dricommon.h:42: error: expected specifier-qualifier-list before 'XID'
va_dricommon.h:49: warning: empty declaration
va_dricommon.h:57: error: expected specifier-qualifier-list before 'drm_handle_t'
va_dricommon.h:69: warning: empty declaration
va_dricommon.h:71: error: expected ')' before 'ctx'
va_dricommon.h:72: error: expected ')' before 'ctx'
va_dricommon.h:73: error: expected ')' before 'ctx'
va_dricommon.h:74: error: expected ')' before 'ctx'
va_dricommon.h:75: error: expected ')' before 'ctx'
va_dricommon.h:76: error: expected ')' before 'ctx'
va_dricommon.h:77: error: expected ')' before 'ctx'
dri1_util.c:22: warning: empty declaration
dri1_util.c:25: error: expected ')' before 'ctx'
dri1_util.c:40: error: expected ')' before 'ctx'
dri1_util.c:46: error: expected ')' before 'ctx'
dri1_util.c:52: error: expected ')' before 'ctx'
dri1_util.c:60: error: expected ')' before 'ctx'
dri1_util.c:74: error: expected ')' before 'ctx'
dri1_util.c:156: error: old-style parameter declarations in prototyped function definition
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/X11/Xlib.h:3577: error: parameter name omitted
dri1_util.c:156: error: expected '{' at end of input
make[3]: *** [dri1_util.lo] Error 1
make[3]: Leaving directory `/home/labtop/libva-1.0.16/va/x11'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/labtop/libva-1.0.16/va'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/labtop/libva-1.0.16'
make: *** [all] Error 2


```

and i think it is beause ioccom.h so i installed libc6-dev, but i have the same error.
i need some help :(

---

