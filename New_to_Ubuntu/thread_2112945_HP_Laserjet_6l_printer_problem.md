---
title: "HP Laserjet 6l printer problem"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by ernsttremel on 2013-02-06
For my HP Laserjet 6l printer I installed the newest drivers "hplip" (hplip-3.12.11) from [http://hplipopensource.com/hplip-weball/index.html](http://hplipopensource.com/hplip-weball/index.html) following the instructions given there. Before there was installed the previous version (hplip-3.11.3a).
After doing so I added my HP Laserjet 6l printer.
But when I tried to print the testpage my printer only printed "rubbish".
How can I resolve ths problem?

Added informations:
attribute hp laserjet 6l.jpeg
eigenschaften.jpeg

troubleshoot.txt=
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Hewlett-Packard-HP-LaserJet-6L (default)>,
 'cups_instance': None,
 'cups_queue': 'Hewlett-Packard-HP-LaserJet-6L',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'Hewlett-Packard HP LaserJet 6L',
                       'printer-is-shared': True,
                       'printer-location': u'UbuntuErnst',
                       'printer-make-and-model': u'HP LaserJet 6L Foomatic/ljet4 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8564740,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-6L'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.6.1',
                                 'device-uri': u'parallel:/dev/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.adobe-reader-postscript',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-pdf-banner',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/urf',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-ids-supported': True,
                                 'job-k-limit': 0,
                                 'job-k-octets-supported': (0, 75885664),
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'jpeg-k-octets-supported': (0, 75885664),
                                 'jpeg-x-dimension-supported': (0, 65535),
                                 'jpeg-y-dimension-supported': (1, 65535),
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [1270],
                                 'media-col-default': '(unknown IPP value tag 0x34)',
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'iso_a4_210x297mm',
                                 'media-left-margin-supported': [635],
                                 'media-right-margin-supported': [635],
                                 'media-size-supported': ['(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)',
                                                          '(unknown IPP value tag 0x34)'],
                                 'media-source-supported': [u'auto',
                                                            u'top',
                                                            u'middle',
                                                            u'bottom',
                                                            u'by-pass-tray',
                                                            u'auto',
                                                            u'envelope',
                                                            u'manual'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'oe_11x17in_11x17in',
                                                     u'iso_a3_297x420mm',
                                                     u'iso_a5_148x210mm',
                                                     u'jis_b5_182x257mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_dl_110x220mm',
                                                     u'om_env-isob5_176.04x250.12mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_legal_8.5x14in',
                                                     u'custom_min_0.5x0.5in',
                                                     u'custom_max_35277.78x35277.78mm'],
                                 'media-top-margin-supported': [1270],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          14,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          56,
                                                          57,
                                                          59,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423,
                                                          14],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'output-mode-default': u'monochrome',
                                 'output-mode-supported': [u'monochrome'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdf-k-octets-supported': (0, 75885664),
                                 'pdf-versions-supported': [u'adobe-1.2',
                                                            u'adobe-1.3',
                                                            u'adobe-1.4',
                                                            u'adobe-1.5',
                                                            u'adobe-1.6',
                                                            u'adobe-1.7',
                                                            u'iso-19005-1_2005',
                                                            u'iso-32000-1_2008',
                                                            u'pwg-5102.3'],
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-color-mode-default': u'monochrome',
                                 'print-color-mode-supported': [u'monochrome'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': u'Hewlett-Packard HP LaserJet 6L @ UbuntuErnst',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/Hewlett-Packard-HP-LaserJet-6L.png',
                                 'printer-info': u'Hewlett-Packard HP LaserJet 6L',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'UbuntuErnst',
                                 'printer-make-and-model': u'HP LaserJet 6L Foomatic/ljet4 (recommended)',
                                 'printer-more-info': u'http://localhost:631/printers/Hewlett-Packard-HP-LaserJet-6L',
                                 'printer-name': u'Hewlett-Packard-HP-LaserJet-6L',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': (300, 300, 3),
                                 'printer-resolution-supported': [(75,
                                                                   75,
                                                                   3),
                                                                  (150,
                                                                   150,
                                                                   3),
                                                                  (300,
                                                                   300,
                                                                   3),
                                                                  (600,
                                                                   600,
                                                                   3)],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1360061136,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8564740,
                                 'printer-up-time': 1360061850,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-6L'],
                                 'printer-uuid': u'urn:uuid:de168b83-a360-37b9-64a4-25986578ee16',
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none'],
                                 'which-jobs-supported': [u'completed',
                                                          u'not-completed',
                                                          u'aborted',
                                                          u'all',
                                                          u'canceled',
                                                          u'pending',
                                                          u'pending-held',
                                                          u'processing',
                                                          u'processing-stopped']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {},
                               u'General': {u'InputSlot': u'Default',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'300x300dpi'},
                               u'JCL': {u'Copies': u'1',
                                        u'Economode': u'Off',
                                        u'MPTray': u'First',
                                        u'Manualfeed': u'Off',
                                        u'REt': u'Medium',
                                        u'TonerDensity': u'3'},
                               u'Miscellaneous': {}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 14427L,
 'error_log_debug_logging_set': True}
Page 7 (Print test page):
{'test_page_attempted': '05/Feb/2013:11:58:42 +0000',
 'test_page_job_id': [128],
 'test_page_job_status': [(True,
                           128,
                           'Hewlett-Packard-HP-LaserJet-6L',
                           'Test Page',
                           'Ausf\xc3\xbchrung l\xc3\xa4uft',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-de',
                            'document-format': u'application/vnd.cups-pdf-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 128,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'http://localhost:631/jobs/128',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1360061948,
                            'job-printer-uri': u'ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-6L',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/128',
                            'job-uuid': u'urn:uuid:e640f9c3-7e45-3a2c-6a5c-bdd2d807560d',
                            'number-of-documents': 1,
                            'printer-uri': u'ipp://localhost/printers/Hewlett-Packard-HP-LaserJet-6L',
                            'time-at-completed': None,
                            'time-at-creation': 1360061922,
                            'time-at-processing': 1360061922})],
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] 2.0 Get-Jobs 35',
               'D [05/Feb/2013:11:58:05 +0100] Get-Jobs ipp://localhost/printers/',
               'D [05/Feb/2013:11:58:05 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] 2.0 Get-Jobs 36',
               'D [05/Feb/2013:11:58:05 +0100] Get-Jobs ipp://localhost/printers/',
               'D [05/Feb/2013:11:58:05 +0100] [Job 127] Loading attributes...',
               'D [05/Feb/2013:11:58:05 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:58:05 +0100] [Client 20] 2.0 Create-Printer-Subscription 37',
               'D [05/Feb/2013:11:58:05 +0100] Create-Printer-Subscription /',
               'D [05/Feb/2013:11:58:05 +0100] cupsdCreateSubscription(con=0xb79b44d0(20), uri="/")',
               'D [05/Feb/2013:11:58:05 +0100] pullmethod="ippget"',
               'D [05/Feb/2013:11:58:05 +0100] notify-lease-duration=86400',
               'D [05/Feb/2013:11:58:05 +0100] notify-time-interval=0',
               'D [05/Feb/2013:11:58:05 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [05/Feb/2013:11:58:05 +0100] Added subscription #1267 for server.',
               'D [05/Feb/2013:11:58:05 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:05 +0100] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [05/Feb/2013:11:58:05 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:07 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:07 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:07 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:58:07 +0100] [Client 20] 2.0 Get-Notifications 38',
               'D [05/Feb/2013:11:58:07 +0100] Get-Notifications /',
               'D [05/Feb/2013:11:58:07 +0100] cupsdIsAuthorized: requesting-user-name="ernst"',
               'D [05/Feb/2013:11:58:07 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2013:11:58:07 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'I [05/Feb/2013:11:58:31 +0100] Generating printcap /var/run/cups/printcap...',
               'I [05/Feb/2013:11:58:31 +0100] Saving subscriptions.conf...',
               'D [05/Feb/2013:11:58:31 +0100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"',
               'D [05/Feb/2013:11:58:32 +0100] [Client 22] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:58:32 +0100] [Client 22] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:32 +0100] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"',
               'D [05/Feb/2013:11:58:32 +0100] [Client 22] Authorized as ernst using PeerCred',
               'D [05/Feb/2013:11:58:32 +0100] [Client 22] 2.0 Renew-Subscription 61',
               'D [05/Feb/2013:11:58:32 +0100] Renew-Subscription /',
               'D [05/Feb/2013:11:58:32 +0100] cupsdIsAuthorized: username="ernst"',
               'D [05/Feb/2013:11:58:32 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:32 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"',
               'D [05/Feb/2013:11:58:32 +0100] Returning IPP successful-ok for Renew-Subscription (/) from localhost',
               'D [05/Feb/2013:11:58:32 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:33 +0100] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [05/Feb/2013:11:58:33 +0100] cupsdNetIFUpdate: "eth0" = 192.168.0.102:631',
               'D [05/Feb/2013:11:58:33 +0100] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [05/Feb/2013:11:58:33 +0100] cupsdNetIFUpdate: "eth0" = [v1.fe80::21e:8cff:fe5e:ed2e+eth0]:631',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] POST /printers/Hewlett-Packard-HP-LaserJet-6L HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] 2.0 Print-Job 39',
               'D [05/Feb/2013:11:58:42 +0100] Print-Job ipp://localhost/printers/Hewlett-Packard-HP-LaserJet-6L',
               'D [05/Feb/2013:11:58:42 +0100] [Job ???] Auto-typing file...',
               'I [05/Feb/2013:11:58:42 +0100] [Job ???] Request file type is application/vnd.cups-pdf-banner.',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(----J-)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] add_job: requesting-user-name="ernst"',
               'D [05/Feb/2013:11:58:42 +0100] Adding default job-sheets values "none,none"...',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Adding start banner page "none".',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(----J-)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Adding end banner page "none".',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] File of type application/vnd.cups-pdf-banner queued by "ernst".',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] hold_until=0',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Queued on "Hewlett-Packard-HP-LaserJet-6L" by "ernst".',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] time-at-processing=1360061922',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(----J-)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] job-sheets=none,none',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[0]="Hewlett-Packard-HP-LaserJet-6L"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[1]="128"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[2]="ernst"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[3]="Test Page"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[4]="1"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[5]="job-uuid=urn:uuid:e640f9c3-7e45-3a2c-6a5c-bdd2d807560d job-originating-host-name=localhost time-at-creation=1360061922 time-at-processing=1360061922"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] argv[6]="/var/spool/cups/d00128-001"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[10]="SERVER_ADMIN=root@UbuntuErnst"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[11]="SOFTWARE=CUPS/1.6.1"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[13]="USER=root"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[14]="CUPS_MAX_MESSAGE=2047"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[17]="IPP_PORT=631"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[18]="CHARSET=utf-8"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[19]="LANG=de_DE.UTF-8"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[20]="PPD=/etc/cups/ppd/Hewlett-Packard-HP-LaserJet-6L.ppd"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[21]="RIP_MAX_CACHE=128m"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[23]="DEVICE_URI=parallel:/dev/lp0"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[24]="PRINTER_INFO=Hewlett-Packard HP LaserJet 6L"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[25]="PRINTER_LOCATION=UbuntuErnst"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[26]="PRINTER=Hewlett-Packard-HP-LaserJet-6L"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[27]="PRINTER_STATE_REASONS=none"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[28]="CUPS_FILETYPE=document"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[29]="FINAL_CONTENT_TYPE=printer/Hewlett-Packard-HP-LaserJet-6L"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] envp[30]="AUTH_I****"',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Started filter /usr/lib/cups/filter/bannertopdf (PID 7125)',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Started filter /usr/lib/cups/filter/pdftopdf (PID 7126)',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7127)',
               'I [05/Feb/2013:11:58:42 +0100] [Job 128] Started backend /usr/lib/cups/backend/parallel (PID 7128)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Hewlett-Packard-HP-LaserJet-6L) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] [Notifier] state=3',
               'D [05/Feb/2013:11:58:42 +0100] [Notifier] state=3',
               'D [05/Feb/2013:11:58:42 +0100] [Notifier] state=3',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] STATE: +connecting-to-device',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(----J-)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Notifier] state=3',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Getting input from file',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] foomatic-rip version 4.0.17.256 running...',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Parsing PPD file ...',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option ColorSpace',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option PageSize',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option ImageableArea',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option PaperDimension',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option InputSlot',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option Manualfeed',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option Economode',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option Copies',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] PID 7125 (/usr/lib/cups/filter/bannertopdf) exited with no errors.',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option Resolution',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option REt',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option TonerDensity',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option MPTray',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Added option Font',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Parameter Summary',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] -----------------',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Spooler: cups',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Printer: Hewlett-Packard-HP-LaserJet-6L',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Shell: /bin/bash',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] PPD file: /etc/cups/ppd/Hewlett-Packard-HP-LaserJet-6L.ppd',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] ATTR file:',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Printer model: HP LaserJet 6L Foomatic/ljet4 (recommended)',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Job title: Test Page',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] File(s) to be printed:',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] <STDIN>',
               "D [05/Feb/2013:11:58:42 +0100] [Job 128] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Printing system options:',
               "D [05/Feb/2013:11:58:42 +0100] [Job 128] Pondering option 'job-uuid=urn:uuid:e640f9c3-7e45-3a2c-6a5c-bdd2d807560d'",
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Unknown option job-uuid=urn:uuid:e640f9c3-7e45-3a2c-6a5c-bdd2d807560d.',
               "D [05/Feb/2013:11:58:42 +0100] [Job 128] Pondering option 'job-originating-host-name=localhost'",
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Unknown option job-originating-host-name=localhost.',
               "D [05/Feb/2013:11:58:42 +0100] [Job 128] Pondering option 'time-at-creation=1360061922'",
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Unknown option time-at-creation=1360061922.',
               "D [05/Feb/2013:11:58:42 +0100] [Job 128] Pondering option 'time-at-processing=1360061922'",
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Unknown option time-at-processing=1360061922.',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Options from the PPD file:',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] ================================================',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] File: <STDIN>',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] ================================================',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Filetype: PDF',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Storing temporary files in /var/spool/cups/tmp',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] PID 7126 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] STATE: -connecting-to-device',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(----J-)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Notifier] state=3',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] File contains 1 pages',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -dNOINTERPOLATE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-PwB7ia',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Starting process "kid3" (generation 1)',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Starting process "kid4" (generation 2)',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] Starting process "renderer" (generation 2)',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] JCL: \x1b%-12345X@PJL',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET MPTRAY=FIRST',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET DENSITY=3',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET RET=MEDIUM',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET COPIES=1',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET ECONOMODE=OFF',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] @PJL SET MANUALFEED=OFF',
               'D [05/Feb/2013:11:58:42 +0100] [Job 128] <job data> \x1b%-12345X@PJL RESET',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] 2.0 Get-Notifications 40',
               'D [05/Feb/2013:11:58:42 +0100] Get-Notifications /',
               'D [05/Feb/2013:11:58:42 +0100] cupsdIsAuthorized: requesting-user-name="ernst"',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] HTTP_WAITING Closing on EOF',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] Closing connection.',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 23] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] HTTP_WAITING Closing on EOF',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] Closing connection.',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 20] 2.0 Get-Notifications 41',
               'D [05/Feb/2013:11:58:42 +0100] Get-Notifications /',
               'D [05/Feb/2013:11:58:42 +0100] cupsdIsAuthorized: requesting-user-name="ernst"',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] 2.0 CUPS-Get-Printers 42',
               'D [05/Feb/2013:11:58:42 +0100] CUPS-Get-Printers',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] 2.0 CUPS-Get-Classes 43',
               'D [05/Feb/2013:11:58:42 +0100] CUPS-Get-Classes',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] POST / HTTP/1.1',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] No authentication data provided.',
               'D [05/Feb/2013:11:58:42 +0100] [Client 25] 2.0 CUPS-Get-Default 44',
               'D [05/Feb/2013:11:58:42 +0100] CUPS-Get-Default',
               'D [05/Feb/2013:11:58:42 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Feb/2013:11:58:42 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Read 4096 bytes of print data.',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] STATE: -media-empty-warning',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] STATE: -offline-report',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Wrote 4096 bytes of print data...',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Read 8192 bytes of print data.',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] renderer exited with status 0',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Wrote 8192 bytes of print data...',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Read 8192 bytes of print data.',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Wrote 8192 bytes of print data...',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Read 8192 bytes of print data.',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Wrote 8192 bytes of print data...',
               'D [05/Feb/2013:11:58:43 +0100] [Job 128] Read 8192 bytes of print data.',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] Wrote 8192 bytes of print data...',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] Read 8192 bytes of print data.',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] kid4 exited with status 0',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] kid3 finished',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] Kid3 exit status: 0',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] Closing foomatic-rip.',
               'D [05/Feb/2013:11:58:44 +0100] [Job 128] PID 7127 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'I [05/Feb/2013:11:59:04 +0100] Saving job.cache...',
               'I [05/Feb/2013:11:59:04 +0100] Saving subscriptions.conf...',
               'D [05/Feb/2013:11:59:04 +0100] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:04 +0100] Report: clients=4',
               'D [05/Feb/2013:11:59:04 +0100] Report: jobs=2',
               'D [05/Feb/2013:11:59:04 +0100] Report: jobs-active=1',
               'D [05/Feb/2013:11:59:04 +0100] Report: printers=1',
               'D [05/Feb/2013:11:59:04 +0100] Report: printers-implicit=0',
               'D [05/Feb/2013:11:59:04 +0100] Report: stringpool-string-count=2846',
               'D [05/Feb/2013:11:59:04 +0100] Report: stringpool-alloc-bytes=11536',
               'D [05/Feb/2013:11:59:04 +0100] Report: stringpool-total-bytes=56864',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Active clients and printing jobs", busy="Printing jobs"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:59:08 +0100] [Job 127] Unloading...',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] 2.0 Get-Job-Attributes 45',
               'D [05/Feb/2013:11:59:08 +0100] Get-Job-Attributes ipp://localhost/jobs/128',
               'D [05/Feb/2013:11:59:08 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/128) from localhost',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Printing jobs", busy="Active clients and printing jobs"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] POST / HTTP/1.1',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Active clients and printing jobs", busy="Printing jobs"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] 2.0 Cancel-Subscription 46',
               'D [05/Feb/2013:11:59:08 +0100] Cancel-Subscription /',
               'D [05/Feb/2013:11:59:08 +0100] cupsdIsAuthorized: requesting-user-name="ernst"',
               'D [05/Feb/2013:11:59:08 +0100] cupsdMarkDirty(-----S)',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and printing jobs"',
               'D [05/Feb/2013:11:59:08 +0100] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] No authentication data provided.',
               'D [05/Feb/2013:11:59:08 +0100] cupsdIsAuthorized: username=""',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] Closing connection.',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] Accepted from localhost (Domain)',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [05/Feb/2013:11:59:08 +0100] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:08 +0100] [Client 20] Authorized as ernst using PeerCred',
               'D [05/Feb/2013:11:59:08 +0100] cupsdIsAuthorized: username="ernst"',
               'I [05/Feb/2013:11:59:08 +0100] Installing config file "/etc/cups/cupsd.conf"...',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"',
               'D [05/Feb/2013:11:59:09 +0100] [Client 22] Closing connection.',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:09 +0100] [Client 23] Closing connection.',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:09 +0100] [Client 25] Closing connection.',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:09 +0100] [Client 20] Closing connection.',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"',
               'D [05/Feb/2013:11:59:09 +0100] cupsdDeregisterPrinter(p=0xb7980690(Hewlett-Packard-HP-LaserJet-6L), removeit=1)',
               'I [05/Feb/2013:11:59:09 +0100] Saving subscriptions.conf...',
               'D [05/Feb/2013:11:59:09 +0100] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"',
               'E [05/Feb/2013:11:59:09 +0100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.',
               'W [05/Feb/2013:11:59:09 +0100] No limit for Validate-Job defined in policy default and no suitable template found.',
               "W [05/Feb/2013:11:59:09 +0100] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.",
               "W [05/Feb/2013:11:59:09 +0100] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.",
               "W [05/Feb/2013:11:59:09 +0100] No limit for Close-Job defined in policy default - using Send-Document's policy.",
               'W [05/Feb/2013:11:59:09 +0100] No JobPrivateAccess defined in policy default - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No JobPrivateValues defined in policy default - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No SubscriptionPrivateAccess defined in policy default - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No SubscriptionPrivateValues defined in policy default - using defaults.',
               "W [05/Feb/2013:11:59:09 +0100] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.",
               "W [05/Feb/2013:11:59:09 +0100] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.",
               "W [05/Feb/2013:11:59:09 +0100] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.",
               "W [05/Feb/2013:11:59:09 +0100] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.",
               'W [05/Feb/2013:11:59:09 +0100] No JobPrivateAccess defined in policy authenticated - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No JobPrivateValues defined in policy authenticated - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.',
               'W [05/Feb/2013:11:59:09 +0100] No SubscriptionPrivateValues defined in policy authenticated - using defaults.',
               "W [05/Feb/2013:11:59:09 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Hewlett-Packard-HP-LaserJet-6L-Gray..' already exists",
               "W [05/Feb/2013:11:59:09 +0100] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Hewlett-Packard-HP-LaserJet-6L' already exists"],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'de_DE',
 'user_locale_messages': 'de_DE'}

---

### Post by ernsttremel on 2013-02-06
I uninstalled HPLIP ( $ sudo apt-get remove --purge hplip )

Then I tried to run an older version of HPLIP (This one under which my printer before had been working correctly)
-$ cd Desktop
~/Desktop$ sh hplip-3.11.3a.run

But I couldn't achieve:

CF. the following:

Creating directory hplip-3.11.3a
Verifying archive integrity... All good.
Uncompressing HPLIP 3.11.3a Self Extracting Archive.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.11.3a)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Thu-07-Feb-2013_00:32:22.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : c

Initializing. Please wait...
\Gtk-Message: Failed to load module "gtk-vector-screenshot"
 

INTRODUCTION
------------
This installer will install HPLIP version 3.11.3a on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 12.10.

Is "Ubuntu 12.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


SELECT HPLIP OPTIONS
--------------------
You can select which HPLIP options to enable. Some options require extra dependencies.

Do you wish to enable 'Network/JetDirect I/O' (y=yes*, n=no, q=quit) ? n
Do you wish to enable 'Graphical User Interfaces (Qt4)' (y=yes*, n=no, q=quit) ? y
Do you wish to enable 'PC Send Fax support' (y=yes*, n=no, q=quit) ? n
Do you wish to enable 'Scanning support' (y=yes*, n=no, q=quit) ? n
Do you wish to enable 'HPLIP documentation (HTML)' (y=yes*, n=no, q=quit) ? n


ENTER USER PASSWORD
-------------------
Please enter the user (ernst)'s password: 
Password accepted


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


READY TO BUILD AND INSTALL
--------------------------
Ready to perform build and install. Press <enter> to continue or 'q' to quit: 


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --prefix=/usr --enable-qt4 --disable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --enable-foomatic-ppd-install --enable-hpijs-install --disable-policykit --disable-cups-drv-install --disable-hpcups-install --disable-network-build --enable-dbus-build --disable-scan-build --disable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
error: 'make' command failed with status code 2
ernst@UbuntuErnst:~/Desktop$ sh hplip-3.11.3a.run
Creating directory hplip-3.11.3a
Verifying archive integrity... All good.
Uncompressing HPLIP 3.11.3a Self Extracting Archive.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.11.3a)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Thu-07-Feb-2013_00:34:06.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
\Gtk-Message: Failed to load module "gtk-vector-screenshot"
 

INTRODUCTION
------------
This installer will install HPLIP version 3.11.3a on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 12.10.

Is "Ubuntu 12.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the user (ernst)'s password: 
Password accepted


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical scanner frontend for SANE)
warning: This installer cannot install 'xsane' for your distro/OS and/or version.
 

PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --prefix=/usr --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --enable-foomatic-ppd-install --enable-hpijs-install --disable-policykit --disable-cups-drv-install --disable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
[SIZE=4][COLOR=Red]error: 'make' command failed with status code 2[/COLOR][/SIZE]
ernst@UbuntuErnst:~/Desktop$ 

The recommended driver for my printer is:

"HP LaserJet 6L Foomatic/ljet4"

But I do not know where from to get it
and
how to install it

---

