---
title: "How to keep this script running always?"
date: 2015-11-10
forum: Programming Talk
---

### Post by vasa1 on 2015-11-10
I'm trying to make a script that will *pkill* an application, google-chrome, if the total %cpu exceeds a certain value but I'm stuck because the script terminates after it pkills the application the first time.

```
#!/bin/bash

if pgrep chrome

then

  sleep_period=10s

  while true; do
    high="$(ps -eo %C --sort -%cpu | awk 'NR==2')"
      if ps -eo %C --sort -%cpu | awk 'NR==2 { exit !($1>40); }'; then
         pkill chrome
      fi
  sleep ${sleep_period}
done
fi
```

The *pgrep chrome* step checks if google-chrome is running.
Then, I set a sleep period of 10s to check after every 10s whether the total %cpu exceeds 40. If it does, *pkill chrome* should execute.

My problem is that once *pkill chrome* runs, my script terminates. I don't want it to terminate. How do I ensure that it keeps running?

Sorry for the bad formatting. I'm just a novice at coding.

---

### Post by sudodus on 2015-11-10
I suggest that you add a while loop outside your if statement.

Example:
```
while true
do
 sleep 1
 clear
 date
done
```

Such a simple loop is killed with ***ctrl+C***. You can make it nicer by checking for input and quitting if you press ***q*** ...

---

### Post by tgalati4 on 2015-11-10
Using a script to kill a program seems like an un-Linux method to improve performance.  Perhaps tweak Chrome to work better:

[http://superuser.com/questions/697567/how-to-reduce-google-chromes-cpu-usage](http://superuser.com/questions/697567/how-to-reduce-google-chromes-cpu-usage)

[http://smallbusiness.chron.com/fix-high-cpu-usage-google-chrome-77171.html](http://smallbusiness.chron.com/fix-high-cpu-usage-google-chrome-77171.html)

When you look at an individual chrome process, no wonder it is such a hog:

> tgalati4 14923  3819  0 Nov08 ?        00:00:57 /opt/google/chrome/chrome --type=renderer --enable-display-list-2d-canvas --enable-experimental-canvas-features --lang=en-US --force-fieldtrials=*AffiliationBasedMatching/Enabled/AppBannerTriggering/Control/AudioProcessing48kHzSupport/Default/*AutofillClassifier/Enabled/CaptivePortalInterstitial/Enabled/*ChildAccountDetection/Disabled/ChromeDashboard/Default/ChromotingQUIC/Disabled/*ClientSideDetectionModel/Model0/DataReductionProxyUseDataSaverOnVPN/Enabled/*DomRel-Enable/enable/EnableGoogleCachedCopyTextExperiment/Button/*EnhancedBookmarks/Default/*ExtensionContentVerification/Enforce/*ExtensionDeveloperModeWarning/Default/*ExtensionInstallVerification/None/InstanceID/Enabled/*NewProfileManagement/Enabled/*NewVideoRendererTrial/Enabled/*OmniboxBundledExperimentV1/StableHQPFrequencyBugFix_PrePeriod_1/*PasswordGeneration/Disabled/PasswordLinkInSettings/Enabled/*PrerenderFromOmnibox/OmniboxPrerenderEnabled/*QUIC/EnabledNoId/ReportCertificateErrors/ShowAndPossiblySend/SHA1IdentityUIWarning/Enabled/SHA1ToolbarUIJanuary2016/Warning/SHA1ToolbarUIJanuary2017/Error/*SafeBrowsingIncidentReportingService/Default/SafeBrowsingReportPhishingErrorLink/Disabled/SafeBrowsingSocialEngineeringStrings/Enabled/*SdchPersistence/Enabled/SessionRestoreBackgroundLoading/Restore/*SlimmingPaint/EnableSlimmingPaint/SyncBackingDatabase32K/Enabled/*UMA-Dynamic-Binary-Uniformity-Trial/default/*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_01/*UMA-Uniformity-Trial-50-Percent/group_01/*UseDelayAgnosticAEC/DefaultEnabled/*VarationsServiceControl/Interval_30min/VoiceTrigger/Install/ --enable-crash-reporter=AD09CB37-552B-45B7-9E46-AD84005D81AD --enable-offli


---

### Post by vasa1 on 2015-11-12
> **tgalati4 said:**
> Using a script to kill a program seems like an un-Linux method to improve performance.  Perhaps tweak Chrome to work work better:
...
I used to play around with Chrome's *about:flags* settings when it was my regular browser some years ago, but now I use it just for very specific tasks. 

My interest came about when I saw this question, [http://unix.stackexchange.com/questions/241553/too-many-tabs-in-chrome-causes-whole-computer-to-freeze](http://unix.stackexchange.com/questions/241553/too-many-tabs-in-chrome-causes-whole-computer-to-freeze) ...

---

### Post by tgalati4 on 2015-11-12
There is a Chrome extension called EZ Tab Killer, that I have not used, but is supposed to help with memory management by allowing quick tab killing, but keeping the tab web link so that you can go back when you need to.  There is also a The Great Suspender which automatically frees up RAM for idle tabs--again I have not used it, so can't comment on how well it works.

---

### Post by lownaimail on 2015-11-12
EZ Tab Killer is nice, but I recommend The Great Suspender. It helps so much if you have dozens of tab opened at once.

---

### Post by tgalati4 on 2015-11-12
I am testing both extensions, but Chrome has grown into a monster RAM-eater.

---

