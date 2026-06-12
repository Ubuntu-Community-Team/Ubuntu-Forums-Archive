---
title: "Grep Problem"
date: 2007-06-19
forum: Programming Talk
---

### Post by g3k0 on 2007-06-19
Hey there.  Grep isnt working for me.  It should be returning 10 numbers when i do this.
```
grep 'Staples Item No.&nbsp;[0-9][0-9]*' -o | grep '[0-9][0-9]*' -o  > test.out

```

Instead it is only returning 1.
I paste the grep command and then press enter and paste the following html. followed with enter and Ctrl D

Please help, it will speed up an extremely monotonous task for me at work.

```

      	      </A></td></tr><td><img src="/images/store/trans.gif" border="0"></td></table></td></tr></table><table width="100%" border="0" cellspacing="0" cellpadding="0"><tr><td bgcolor="#FFFFCC"><img src="/images/store/spacer.gif" width="100%" height="10"></td></tr><tr><td><img src="/images/store/1x1_drkgray_spacer.gif" width="100%" height="1"></td></tr><tr><td><img src="/images/store/spacer.gif" width="100%" height="10"></td></tr></table><table width="100%" border="0" cellpadding="3" cellspacing="1"><form name="PaginationForm" action="" method="post"><tr><td colspan="7" nowrap="true"><table width="100%" border="0" cellpadding="4" cellspacing="0"><tr><td><img src="/images/store/trans.gif" border="0"></td><td width="75" nowrap="true" class="pagination">Page&nbsp;1&nbsp;of&nbsp;2</td><td width="50"><A href="javascript:subSearchSubmit('page','2');"><img src="/images/store/next_btn.gif" width="49" height="15" alt="Next" border="0"></A></td></tr></table></td></tr></form><tr><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">Customer Item No.</td><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">MFR Item No.</td><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">UOM/QTY</td><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">Your Price</td><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">Qty</td><td class="libodygrey" bgcolor="#CCCCCC" align="center" valign="middle">Add to....</td></tr><tr><td><table border="0" width="100%" cellspacing="0" cellpadding="0"><tr><td><a href="javascript:subSetCookieHelper('ShowHideImages','show');subSearchSubmit('','');"><img src="/images/store/showimages.gif" border="0" alt="Hide Images"></a></td></tr></table></td></tr><form name="R51808775N11141131" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51808775N11141131,'51808775','EA','1','0','512753','18.94','N','ZZZZZZZZZZZZZZZZZZZZZ','18.94','00000000','RC','00');">Targus Ultra Mini Optical Mouse</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;512753</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">PAUM01U</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$18.94</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51808775N11141131,'51808775','EA','1','0','512753','18.94','N','ZZZZZZZZZZZZZZZZZZZZZ','18.94','00000000','RC','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51808775N11141131,'51808775','EA','1','0','512753','18.94','N','ZZZZZZZZZZZZZZZZZZZZZ','18.94','00000000','RC','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51867937N11141132" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51867937N11141132,'51867937','EA','1','0','571469','9.15','N','ZZZZZZZZZZZZZZZZZZZZZ','9.15','00000000','VM','00');">Logitech Click! Optical Mouse</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;571469</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">LOG9312220403</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$9.15</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51867937N11141132,'51867937','EA','1','0','571469','9.15','N','ZZZZZZZZZZZZZZZZZZZZZ','9.15','00000000','VM','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51867937N11141132,'51867937','EA','1','0','571469','9.15','N','ZZZZZZZZZZZZZZZZZZZZZ','9.15','00000000','VM','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R1524190N11141133" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R1524190N11141133,'1524190','EA','1','0','395496','39.99','N','ZZZZZZZZZZZZZZZZZZZZZ','39.99','00000000','FX','00');">Logitech Trackman Wheel</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;395496</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">LOG9043530403</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$39.99</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R1524190N11141133,'1524190','EA','1','0','395496','39.99','N','ZZZZZZZZZZZZZZZZZZZZZ','39.99','00000000','FX','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R1524190N11141133,'1524190','EA','1','0','395496','39.99','N','ZZZZZZZZZZZZZZZZZZZZZ','39.99','00000000','FX','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51854959N11141134" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51854959N11141134,'51854959','EA','1','0','520247','32.23','N','ZZZZZZZZZZZZZZZZZZZZZ','32.23','00000000','RC','00');">Kensington PilotMouse Optical</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;520247</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">KMW72127</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$32.23</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51854959N11141134,'51854959','EA','1','0','520247','32.23','N','ZZZZZZZZZZZZZZZZZZZZZ','32.23','00000000','RC','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51854959N11141134,'51854959','EA','1','0','520247','32.23','N','ZZZZZZZZZZZZZZZZZZZZZ','32.23','00000000','RC','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51948002N11141135" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51948002N11141135,'51948002','EA','1','0','636359','38.03','N','ZZZZZZZZZZZZZZZZZZZZZ','38.03','00000000','RC','00');">Targus®  Wireless Laser Notebook Mouse</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;636359</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">AMW15U</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$38.03</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51948002N11141135,'51948002','EA','1','0','636359','38.03','N','ZZZZZZZZZZZZZZZZZZZZZ','38.03','00000000','RC','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51948002N11141135,'51948002','EA','1','0','636359','38.03','N','ZZZZZZZZZZZZZZZZZZZZZ','38.03','00000000','RC','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R56723N11141136" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R56723N11141136,'56723','EA','1','0','378863','19.99','N','ZZZZZZZZZZZZZZZZZZZZZ','19.99','00000000','FX','00');">Logitech Marble Mouse</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;378863</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">LOG9043600403</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$19.99</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R56723N11141136,'56723','EA','1','0','378863','19.99','N','ZZZZZZZZZZZZZZZZZZZZZ','19.99','00000000','FX','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R56723N11141136,'56723','EA','1','0','378863','19.99','N','ZZZZZZZZZZZZZZZZZZZZZ','19.99','00000000','FX','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51811408N11141137" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51811408N11141137,'51811408','EA','1','0','510824','87.99','N','ZZZZZZZZZZZZZZZZZZZZZ','87.99','00000000','RC','00');">3M Optical Ergonomic Mouse, Small/Medium, Graphite</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;510824</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">MMMEM500GPS</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$87.99</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51811408N11141137,'51811408','EA','1','0','510824','87.99','N','ZZZZZZZZZZZZZZZZZZZZZ','87.99','00000000','RC','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51811408N11141137,'51811408','EA','1','0','510824','87.99','N','ZZZZZZZZZZZZZZZZZZZZZ','87.99','00000000','RC','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51951828N11141138" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51951828N11141138,'51951828','EA','1','0','663016','49.98','N','ZZZZZZZZZZZZZZZZZZZZZ','49.98','00000000','FX','00');">Logitech® V450 Cordless Notebook Mouse, Silver</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;663016</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">9316690403</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$49.98</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51951828N11141138,'51951828','EA','1','0','663016','49.98','N','ZZZZZZZZZZZZZZZZZZZZZ','49.98','00000000','FX','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51951828N11141138,'51951828','EA','1','0','663016','49.98','N','ZZZZZZZZZZZZZZZZZZZZZ','49.98','00000000','FX','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51820005N11141139" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51820005N11141139,'51820005','EA','1','0','554406','14.99','N','ZZZZZZZZZZZZZZZZZZZZZ','14.99','00000000','FX','00');">Kensington Portable Optical Mouse</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;554406</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">72114</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$14.99</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51820005N11141139,'51820005','EA','1','0','554406','14.99','N','ZZZZZZZZZZZZZZZZZZZZZ','14.99','00000000','FX','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51820005N11141139,'51820005','EA','1','0','554406','14.99','N','ZZZZZZZZZZZZZZZZZZZZZ','14.99','00000000','FX','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="R51921175N111411310" action="" method="post" onSubmit="return bolWarnInvalid(this.quantity_1, 'Please click applicable buttons. Or, you may Tab to these buttons.');"><tr><td colspan="6" class="searchProdDescrip" valign="top" align="left"><table border="0" cellpadding="0" cellspacing="0"><tr><td align="left"><a class="bigund" href="javascript:subAddTo('item',document.R51921175N111411310,'51921175','EA','1','0','622141','32.98','N','ZZZZZZZZZZZZZZZZZZZZZ','32.98','00000000','FX','00');">Cordless Mini Optical Mouse for Notebooks, 7w x 3d x 8-1/2h, Silver</a></td></tr><tr><td><img src="/images/store/trans.gif" border="0" height="3" width="1"></td></tr><tr><td><span class="libignotbld">Staples Item No.&nbsp;622141</span></td></tr></table></td></tr><tr><td class="libody" valign="top" align="center"></td><td class="libody" valign="top" align="center">LOG9313960403</td><td align="center" valign="top"><A href="javascript:subShowLinkHelpWindow('/html/help/stealth/UoM.htm','refurl');" class="smallund">EA/1</A></td><td class="libody" valign="top" align="left">$32.98</td><td class="libody" valign="top" align="center"><input type="text" name="quantity_1" size="2" style="width: 40px;" maxlength="4" value="1" onfocus="this.select()"></td><td class="libody" valign="top" align="top"><table border="0" cellpadding="3" cellspacing="0"><tr><td align="center" valign="top"><a href="javascript:subAddTo('order',document.R51921175N111411310,'51921175','EA','1','0','622141','32.98','N','ZZZZZZZZZZZZZZZZZZZZZ','32.98','00000000','FX','00');"><img src="/images/store/addtoorder.gif" border="0" alt="Add to Order"></a></td></tr><tr><td><a href="javascript:subAddTo('list',document.R51921175N111411310,'51921175','EA','1','0','622141','32.98','N','ZZZZZZZZZZZZZZZZZZZZZ','32.98','00000000','FX','00');"><img src="/images/store/addtolist.gif" border="0" alt="Add to List"></a></td></tr></table></td></tr><tr><td colspan="6"><img src="/images/store/trans.gif" height="1" width="1"></td></tr><tr valign="top" align="left"><td colspan="7"><img width="100%" height="1" src="/images/store/1x1_drkgray_spacer.gif" border="0"></td></tr></form><form name="PaginationForm" action="" method="post"><tr><td colspan="7" nowrap="true"><table width="100%" border="0" cellpadding="4" cellspacing="0"><tr><td><img src="/images/store/trans.gif" border="0"></td><td width="75" nowrap="true" class="pagination">Page&nbsp;1&nbsp;of&nbsp;2</td><td width="50"><A href="javascript:subSearchSubmit('page','2');"><img src="/images/store/next_btn.gif" width="49" height="15" alt="Next" border="0"></A></td></tr></table></td></tr></form></table>
  </td></tr>
  <tr><td width="638"><img src="/images/store/trans.gif" height="1" border="0"></td></tr>
</table>



```

---

### Post by Modred on 2007-06-19
I haven't attempted to run the command, but I'll take a wild shot that this isn't working because you forgot the **-e** flag to grep, which tells it that you're providing a regexp.

---

### Post by g3k0 on 2007-06-19
I tried putting -e= in front of the expression but it came up with no results...

---

### Post by jyba on 2007-06-19
You're using the -o option both times, so both times it only returns the part of the line that matches. The first grep returns...

    **Staples Item No.&nbsp;512753**

...so the second grep can only return one number...

   ** 512753**

Perhaps you meant to to do this instead?...
```
grep 'Staples Item No.&nbsp;[0-9][0-9]*' | grep -o '[0-9][0-9]*' > test.out
```

---

### Post by g3k0 on 2007-06-19
The first -o cleans out all the unneccessary areas because what im looking for comes right after.  the first should return 
Staples Item No.&nbsp;512753
Staples Item No.&nbsp;571469
Staples Item No.&nbsp;395496
Staples Item No.&nbsp;520247
Staples Item No.&nbsp;636359
Staples Item No.&nbsp;378863
Staples Item No.&nbsp;510824
Staples Item No.&nbsp;663016
Staples Item No.&nbsp;554406
Staples Item No.&nbsp;622141

the second -o removes the text leaving only the 10 numbers

---

### Post by jyba on 2007-06-19
Okay, I see now. Perhaps you should **append** the numbers to test.out instead of **overwriting** it each time? ;)

```
grep 'Staples Item No.&nbsp;[0-9][0-9]*' -o | grep '[0-9][0-9]*' -o  >> test.out
```

---

### Post by g3k0 on 2007-06-19
It should only rewrite when you start a new command.  I tried it anway and it still resulted in one output.  It just combined it with the last time I did it.  So I ended up with 
512753
512753

---

### Post by bigboy_pdb on 2007-06-19
I saved the html to a file named 'temp.txt' and used:
cat temp.txt | grep 'Staples Item No\.&nbsp;[0-9][0-9]*' -o | grep '[0-9][0-9]*' -o

and I was returned the results:

512753
571469
395496
520247
636359
378863
510824
663016
554406
622141

It would appear that pasting the text on the screen is what is causing the problem. If you can save the html to a file first and then use 'cat' to send the file to grep (so it can be evaluated line by line) then that would appear to work for now. I'll try to find out why the other method isn't working in the mean time.

EDIT: The first paragraph should read 'copied and pated the html into a file' instead of 'saved the html to a file'

---

### Post by bigboy_pdb on 2007-06-19
EDIT: My first post was correct but this response (which is the reason why I initially thought that pasting the text at the command line didn't work) is incorrect. You may safely ignore it if you wish.

The reason why it doesn't work when you copy and paste the HTML directly is because all of the newlines are not being counted as newlines for the standard input. You can tell because there are no line breaks when you paste it.

What appears to be happening is grep reads the whole thing as one line and it matches only the first pattern that is matched within the line. Since '-o' only makes it print the portion of the pattern that is matched, it prints the first number that you were looking for, which is 512753.

You'll notice that only 'Staples Item No.&nbsp;512753' is printed if you use:
grep 'Staples Item No\.&nbsp;[0-9][0-9]*' -o

Using 'awk' should work for this problem if you cannot save the HTML to a file.

---

### Post by WW on 2007-06-19
The first line of the html sample that you posted contains 23270 characters.  I first tried saving it to a file by entering this command
```

$ cat - > tmp.dat

```
and pasting the text using the mouse (left and middle click).  *Only the first 4096 characters of the first line were saved*.  There is only one occurrence of "Staples Item No" in the first 4096 characters.  When I pasted the text into gedit instead, I was able to get the entire line. Then your command gives:
```

$ grep 'Staples Item No.&nbsp;[0-9][0-9]*' -o tmp.dat | grep '[0-9][0-9]*' -o
512753
571469
395496
520247
636359
378863
510824
663016
554406
622141
$

```

---

### Post by bigboy_pdb on 2007-06-19
I apologize my second post is incorrect. I'm not used to using the -o option with grep.

WW is correct.
I verified what he said by saving the text to a text file called 'temp.txt', copying the text to the command line and then copying and pasting that text to a file called 'temp2.txt', and then I used 'wc --char temp.txt' and 'wc --char temp2.txt' to check the counts of the number of characters in each file. The file 'temp2.txt' had less characters meaning you cannot paste that much text directly to the command line.

This means that you have no other option other than to save the text to a text file and use grep to read it from the file (or to pipe it to the grep program) in order to properly extract the information that you wanted.

Thank you WW for correcting me

---

### Post by g3k0 on 2007-06-20
Thanks for the help guys.  This will save me alot of time.

---

