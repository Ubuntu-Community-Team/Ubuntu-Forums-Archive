---
title: "installing ati drivers from ubuntuI"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-10-15
I just fresh installed ubuntu 11.10 and I am getting the following message when trying to install the ati drivers: ```
please have a look at the log file for details: /var/log/jockey.log 
```

Is there an easy fix for this? I already tried refresh installing 11.10 but it did not work.

---

### Post by ubudog on 2011-10-15
Welcome.

Can you please run this command and post the output here?
```
cat /var/log/jockey.log
```

---

### Post by jiggajoe506 on 2011-10-15
```
kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 18:26:59,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 18:26:59,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 18:26:59,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 18:26:59,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001025sd0000036Ebc01sc01i8a')
2011-10-15 18:26:59,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2011-10-15 18:26:59,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd0000036Ebc01sc06i01')
2011-10-15 18:26:59,685 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 18:26:59,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,685 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 18:26:59,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 18:26:59,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2011-10-15 18:26:59,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2011-10-15 18:26:59,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 18:26:59,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 18:26:59,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 18:26:59,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 18:26:59,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 18:26:59,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 18:26:59,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'usb:v0402p9665d0009dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 18:26:59,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 18:26:59,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'platform:eisa')
2011-10-15 18:26:59,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-10-15 18:26:59,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 18:26:59,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 18:26:59,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 18:26:59,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 18:26:59,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 18:26:59,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 18:26:59,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2011-10-15 18:26:59,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd0000036Ebc0Csc05i00')
2011-10-15 18:26:59,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-10-15 18:26:59,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-10-15 18:26:59,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2011-10-15 18:26:59,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 18:26:59,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 18:26:59,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 18:26:59,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739b64c> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00009712sv00001025sd0000036Ebc03sc00i00')
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 18:26:59,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d0000970Fsv00001025sd0000036Ebc04sc03i00')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:36916B91-1A64-4583-84D0-53830FB9108D')
2011-10-15 18:26:59,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:acer-wmi')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd0000036Ebc0Csc03i20')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00009601sv00001025sd0000036Ebc06sc00i00')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:SYN1B17:SYN1B00:SYN0002:PNP0F13:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00009602sv00001022sd00009602bc06sc04i00')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 18:26:59,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc02sc80i00')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd0000036Ebc06sc01i00')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0003v0402p9665e0009-e0,1,kD4,ramlsfw')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v000014E4d00001692sv00001025sd0000036Ebc02sc00i00')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.04:bd04/23/2010:svnAcer:pnAspire5551:pvrV1.04:rvnAcer:rnAspire5551:rvrV1.04:cvnAcer:ct10:cvrV1.04:')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 18:26:59,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'usb:v0402p9665d0009dcEFdsc02dp01ic0Eisc01ip00')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd0000036Ebc04sc03i00')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001025sd0000036Ebc01sc01i8a')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd0000036Ebc01sc06i01')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'usb:v0402p9665d0009dcEFdsc02dp01ic0Eisc02ip00')
2011-10-15 18:26:59,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'platform:eisa')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd0000036Ebc0Csc05i00')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-15 18:26:59,710 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a906ac> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2011-10-15 18:26:59,744 DEBUG: handler xorg:fglrx_updates previously unseen
2011-10-15 18:26:59,745 DEBUG: handler xorg:fglrx previously unseen
2011-10-15 18:26:59,873 DEBUG: writing back check cache /var/cache/jockey/check
2011-10-15 18:26:59,898 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:26:59,899 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:26:59,924 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:26:59,924 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:26:59,966 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:26:59,966 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:03,382 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:03,382 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:03,550 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:03,550 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:27:03,739 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:03,739 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:03,871 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:03,872 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:03,960 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:03,961 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:27:06,106 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:06,106 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:09,236 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 18:27:09,341 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 18:27:09,503 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:09,504 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:09,549 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:09,549 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,280 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,281 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,336 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,336 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,439 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,440 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:27:11,591 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,592 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,617 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,617 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,716 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,717 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,771 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,772 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:11,869 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:11,870 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:27:12,894 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:12,895 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:12,949 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:12,950 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:13,340 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 18:27:13,443 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 18:27:13,582 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:13,583 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:13,637 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:13,638 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,091 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,092 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,147 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,147 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,251 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,252 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:27:15,456 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,456 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,511 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,512 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,656 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,656 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,710 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,711 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 18:27:15,809 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:27:15,810 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:38:40,359 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:38:40,359 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:38:40,724 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:38:40,725 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:38:41,271 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:38:41,272 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 18:38:41,463 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 18:38:41,464 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking


```

This is what I got

---

### Post by anewguy on 2011-10-15
I have an ATI card that also requires the old fglrx driver.  I get error messages about fglrx_updates as well.  Considering non-existent driver support from ATI, I finally broke down and just bought an nVidia based card today.  I haven't installed it yet, but I'm hoping I get rid of all the problems I've had with ATI with generating new ones for nVidia.

Dave ;)

---

### Post by jiggajoe506 on 2011-10-15
> **anewguy said:**
> I have an ATI card that also requires the old fglrx driver.  I get error messages about fglrx_updates as well.  Considering non-existent driver support from ATI, I finally broke down and just bought an nVidia based card today.  I haven't installed it yet, but I'm hoping I get rid of all the problems I've had with ATI with generating new ones for nVidia.

Dave ;)

Yeah I am just a dumb dumb and like to tinker with things I know nothing about so I brought this on myself.

---

### Post by KingYaba on 2011-10-15
Did the ATI driver work in an earlier version of Ubuntu? If you haven't already, read the installation Wiki because ATI has you install a few things before installing their driver.

[http://wiki.cchtml.com/index.php/Ubuntu#Installation](http://wiki.cchtml.com/index.php/Ubuntu#Installation)

---

### Post by Gs Dewd on 2011-10-16
Also what video card do you have and what problems are you having that are requiring you to update the drivers?

---

### Post by sadaruwan12 on 2011-10-16
I've to second that anewguy, I agree 100% with you I'd a ATI with me the effects and the display was not that nice but I got NVIDIA after installing that I instantly saw the difference graphics was much sharper and prettier text was very clear and I'm not going to look back on ATI again.

---

### Post by jiggajoe506 on 2011-10-16
> **Gs Dewd said:**
> Also what video card do you have and what problems are you having that are requiring you to update the drivers?

I have a ati mobility radeon HD 4250. Its telling me to activate the drivers but it keeps giving me that error message. I am flustered right now.

---

### Post by jiggajoe506 on 2011-10-16
I am trying to get gnome 3 shell to work.

---

### Post by waynefoutz on 2011-10-16
> **jiggajoe506 said:**
> I have a ati mobility radeon HD 4250. Its telling me to activate the drivers but it keeps giving me that error message. I am flustered right now.

I have the same card, was getting the same message in jockey.log. After a reboot, it installed fine. As for gnome-shell, as far as I know, you need to remove the proprietary drivers and go with the open source version. fglrx doesn't get along with gnome-shell at all. I've heard that the latest version, 11.9, from ATI's website has fixed the gnome-shell issues, but I haven't ventured to try it.

---

### Post by jiggajoe506 on 2011-10-22
hey guys just bumping this because it still isn't fixed and I am losing sleep over it ;)

---

### Post by masgeeks on 2011-10-22
Non-proprietary ATI drivers work just fine with unity or gnome shell.  Proprietary fglrx driver causes screen aberrations if you use gnome shell.  I had same issue - I wiped machine since I hadn't gotten far and reinstalled and didn't bother with ATI drivers everything is good.  However, I understand you will not get full 3D support if you do not use the ATI drivers - so gamers would be affected if they want to use gnome shell.  For what I do, the free drivers are just fine...  :)

---

### Post by rsvancara on 2011-10-22
I gave up on the fglrx drivers a long time ago.  They are difficult to make work under Linux.  My two cents...go with the open source drivers.  If you need 3D capabilities, get an nvidia card.  

Randall

[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

### Post by jiggajoe506 on 2011-10-22
I just want gnome 3 to work... I don't game. When I use the shell it always reverts me to the old gnome.

---

