---
title: "Modprobe isn't working"
date: 2018-07-06
forum: New to Ubuntu
---

### Post by mustafa7888 on 2018-07-06
I am trying to overclock my laptop's CPU and for one of the steps i have to type: 'modprobe msr' into the terminal, but when I type that nothing happens.

---

### Post by Holger_Gehrke on 2018-07-07
Like a lot of (non-interactive) Linux programs, modprobe does not give any message on success (No News is Good News). You can check that it has loaded the module into the kernel by getting the list of loaded modules (lsmod) and searching the output for 'msr' ('lsmod|grep 'msr'). Since the module is supposed to give you access to the **M**odell **S**pecific **R**egisters of your processor through pseudo files in '/proc', you can take a look in '/proc/msr'. If that directory exists and has files (and subdirectories) in it, the msr modules is loaded and working.

Holger

---

### Post by mustafa7888 on 2018-07-07
Well now when i type 'modprobe msr' i get "modprobe: ERROR could not insert 'msr': Operation not permitted', so what do I do now?

---

### Post by The Cog on 2018-07-07
sudo modprobe msr

---

### Post by mustafa7888 on 2018-07-07
I figured that out and got to the next part now when i type 'turbostat' i get this long error message of things I need to install that I already have installed

P.S. The link to the image is:
[https://imgur.com/a/UMPHV2h](https://imgur.com/a/UMPHV2h)

---

### Post by #&amp;thj^% on 2018-07-07
Try instead:
```
sudo turbostat
```
The tools needed are related to version of kernel also.
```
 sudo turbostat
turbostat version 17.06.23 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 22 CPUID levels; family:model:stepping 0x6:5e:3 (6:94:3)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM TM
CPUID(6): APERF, TURBO, DTS, PTM, HWP, HWPnotify, HWPwindow, HWPepp, No-HWPpkg, EPB
cpu1: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST No-MWAIT PREFETCH TURBO)
CPUID(7): SGX
cpu1: MSR_IA32_FEATURE_CONTROL: 0x00000005 (Locked )
CPUID(0x15): eax_crystal: 2 ebx_tsc: 226 ecx_crystal_hz: 0
TSC: 2712 MHz (24000000 Hz * 226 / 2 / 1000000)
CPUID(0x16): base_mhz: 2700 max_mhz: 3300 bus_mhz: 100
cpu1: MSR_MISC_PWR_MGMT: 0x00401cc0 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 4033 sec. Joule Counter Range, at 65 Watts
cpu1: MSR_PLATFORM_INFO: 0x80838f1011b00
8 * 100.0 = 800.0 MHz max efficiency frequency
27 * 100.0 = 2700.0 MHz base frequency
cpu1: MSR_IA32_POWER_CTL: 0x0024005d (C1E auto-promotion: DISabled)
cpu1: MSR_TURBO_RATIO_LIMIT: 0x1f202121
31 * 100.0 = 3100.0 MHz max turbo 4 active cores
32 * 100.0 = 3200.0 MHz max turbo 3 active cores
33 * 100.0 = 3300.0 MHz max turbo 2 active cores
33 * 100.0 = 3300.0 MHz max turbo 1 active cores
cpu1: MSR_CONFIG_TDP_NOMINAL: 0x0000001b (base_ratio=27)
cpu1: MSR_CONFIG_TDP_LEVEL_1: 0x00000000 ()
cpu1: MSR_CONFIG_TDP_LEVEL_2: 0x00000000 ()
cpu1: MSR_CONFIG_TDP_CONTROL: 0x80000000 ( lock=1)
cpu1: MSR_TURBO_ACTIVATION_RATIO: 0x00000000 (MAX_NON_TURBO_RATIO=0 lock=0)
cpu1: MSR_PKG_CST_CONFIG_CONTROL: 0x7e008006 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=6: pc8)
cpu1: POLL: CPUIDLE CORE POLL IDLE
cpu1: C1: MWAIT 0x00
cpu1: C1E: MWAIT 0x01
cpu1: C3: MWAIT 0x10
cpu1: C6: MWAIT 0x20
cpu1: C7s: MWAIT 0x33
cpu1: C8: MWAIT 0x40
cpu1: cpufreq driver: intel_pstate
cpu1: cpufreq governor: powersave
cpufreq intel_pstate no_turbo: 0
cpu1: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_PM_ENABLE: 0x00000001 (HWP)
cpu0: MSR_HWP_CAPABILITIES: 0x01101b21 (high 33 guar 27 eff 16 low 1)
cpu0: MSR_HWP_REQUEST: 0x80002108 (min 8 max 33 des 0 epp 0x80 window 0x0 pkg 0x0)
cpu0: MSR_HWP_INTERRUPT: 0x00000000 (Dis_Guaranteed_Perf_Change, Dis_Excursion_Min)
cpu0: MSR_HWP_STATUS: 0x00000004 (No-Guaranteed_Perf_Change, No-Excursion_Min)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x00000208 (65 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x42028a00148208 (UNlocked)
cpu0: PKG Limit #1: ENabled (65.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (81.250000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_DRAM_POWER_LIMIT: 0x5400de00000000 (UNlocked)
cpu0: DRAM Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00641000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88350000 (47 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (100 C, 100 C)
cpu1: MSR_PKGC3_IRTL: 0x0000884e (valid, 79872 ns)
cpu1: MSR_PKGC6_IRTL: 0x00008876 (valid, 120832 ns)
cpu1: MSR_PKGC7_IRTL: 0x00008894 (valid, 151552 ns)
cpu1: MSR_PKGC8_IRTL: 0x000088fa (valid, 256000 ns)
cpu1: MSR_PKGC9_IRTL: 0x0000894c (valid, 339968 ns)
cpu1: MSR_PKGC10_IRTL: 0x00008bf2 (valid, 1034240 ns)
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	1019	31.03	3285	2711	4338	0	519	577	85	305	20	2051	0.41	1.23	0.18	1.24	0.23	65.16	2.53	0.19	1.17	65.08	46	46	125.43	99.66	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	15.17	14.12	0.00	0.46	0.00	0.00
0	0	91	2.86	3181	2711	908	0	101	208	25	86	9	659	0.71	2.26	0.38	1.88	0.46	91.23	3.64	0.39	1.81	91.31	39	46	125.43	99.67	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	15.17	14.12	0.00	0.46	0.00	0.00
1	1	369	11.31	3267	2711	1305	0	87	210	24	134	2	845	0.45	2.04	0.16	1.60	0.01	84.04	3.50	0.14	1.52	83.53	41
2	2	362	11.09	3267	2711	764	0	331	159	36	85	9	547	0.46	0.63	0.18	1.48	0.44	85.36	1.84	0.25	1.34	85.47	37
3	3	3254	98.87	3292	2711	1361	0	0	0	00	0	0	0.00	0.00	0.00	0.00	0.00	0.00	1.13	0.00	0.00	0.00	46
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	1106	33.70	3282	2711	5077	0	364	751	123	542	30	2434	0.67	1.11	0.39	2.25	0.42	60.68	3.03	0.39	2.16	60.72	48	49	136.33	99.30	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	16.26	15.17	0.00	0.46	0.00	0.00
0	0	411	12.57	3266	2711	1089	0	141	308	28	138	11	680	1.27	0.99	0.46	2.40	0.85	80.93	3.28	0.44	2.32	81.38	40	49	136.33	99.30	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	16.26	15.17	0.00	0.46	0.00	0.00
1	1	374	11.49	3260	2711	1539	0	84	196	67	302	8	1019	0.68	2.53	0.87	4.00	0.23	79.72	4.52	0.90	3.80	79.30	41
2	2	401	12.33	3251	2711	1127	0	139	247	28	102	11	735	0.72	0.93	0.21	2.58	0.60	82.06	2.74	0.22	2.51	82.20	37
3	3	3238	98.43	3291	2711	1322	0	0	0	00	0	0	0.00	0.00	0.00	0.00	0.00	0.00	1.57	0.00	0.00	0.00	48
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	1021	31.09	3286	2711	4824	0	750	550	87	330	13	2235	0.68	0.84	0.18	1.24	0.17	65.24	2.47	0.21	1.19	65.05	48	48	125.68	99.61	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	15.55	14.49	0.00	0.46	0.00	0.00
0	0	84	2.66	3175	2711	1005	0	317	216	20	82	1	752	0.75	0.69	0.22	1.23	0.03	94.19	2.16	0.34	1.17	93.67	40	48	125.68	99.61	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	15.55	14.49	0.00	0.46	0.00	0.00
1	1	399	12.20	3267	2711	1624	0	312	247	40	170	2	841	1.53	1.85	0.30	2.76	0.08	80.87	4.43	0.30	2.63	80.44	43
2	2	349	10.69	3261	2711	879	0	121	87	27	78	10	642	0.45	0.83	0.22	0.99	0.57	85.88	2.09	0.20	0.95	86.07	38
3	3	3253	98.80	3294	2711	1316	0	0	0	00	0	0	0.00	0.00	0.00	0.00	0.00	0.00	1.20	0.00	0.00	0.00	48
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	1098	33.42	3286	2711	4911	0	375	758	107	557	49	2689	0.52	1.20	0.22	2.11	0.45	61.25	3.06	0.26	1.99	61.27	48	48	135.24	99.19	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	16.25	15.19	0.00	0.46	0.00	0.00
0	0	390	11.92	3268	2711	1013	0	181	291	46	153	8	911	1.13	0.74	0.35	2.35	0.36	82.59	3.06	0.51	2.13	82.37	40	48	135.24	99.19	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	0.00	16.25	15.19	0.00	0.46	0.00	0.00
1	1	88	2.75	3189	2711	1554	0	121	294	47	333	30	1243	0.67	3.21	0.36	4.36	1.10	87.14	5.27	0.38	4.13	87.47	42
2	2	678	20.70	3279	2711	1030	0	73	173	14	71	11	535	0.29	0.85	0.15	1.75	0.32	75.26	2.20	0.14	1.71	75.25	37
3	3	3236	98.31	3293	2711	1314	0	0	0	00	0	0	0.00	0.00	0.00	0.00	0.00	0.00	1.69	0.00	0.00	0.00	48
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	651	20.99	3103	2711	4439	0	1163	875	168	731	6	3732	0.80	2.82	0.27	2.93	0.06	71.45	5.08	0.28	2.79	70.86	38	41	85.65	65.15	0.00	0.00	30.03	0.00	0.00	0.00	0.00	0.00	0.00	10.37	9.04	0.00	0.47	0.00	0.00
0	0	219	8.29	2645	2711	727	0	371	257	30	187	0	1045	0.80	1.67	0.19	2.52	0.00	86.09	3.73	0.17	2.41	85.40	36	41	85.65	65.15	0.00	0.00	30.03	0.00	0.00	0.00	0.00	0.00	0.00	10.37	9.04	0.00	0.47	0.00	0.00
1	1	416	13.85	3003	2711	1730	0	92	331	46	337	1	1244	1.14	6.25	0.31	5.56	0.01	72.22	9.16	0.28	5.34	71.38	38
2	2	375	12.30	3053	2711	851	0	424	178	62	141	1	812	0.67	2.15	0.29	2.28	0.00	81.74	4.07	0.38	2.09	81.16	35
3	3	1595	49.53	3221	2711	1131	0	276	109	30	66	4	631	0.58	1.23	0.30	1.35	0.21	45.76	3.37	0.29	1.30	45.51	35
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	352	14.67	2397	2712	4883	0	558	804	175	838	58	4431	0.30	1.31	0.39	4.28	0.53	78.32	2.84	0.36	4.13	78.00	38	40	60.60	50.12	0.00	0.00	46.95	0.00	0.00	0.00	0.00	0.00	0.00	5.53	4.14	0.00	0.49	0.00	0.00
0	0	271	13.80	1961	2712	950	0	125	322	28	244	18	1266	0.24	1.05	0.26	4.78	0.47	79.17	2.67	0.25	4.61	78.68	37	40	60.60	50.12	0.00	0.00	46.95	0.00	0.00	0.00	0.00	0.00	0.00	5.53	4.14	0.00	0.49	0.00	0.00
1	1	948	35.25	2689	2712	1737	0	34	111	34	180	0	882	0.05	0.79	0.12	4.04	0.00	59.48	1.96	0.09	3.90	58.81	38
2	2	86	4.46	1937	2712	1234	0	190	127	53	247	18	1221	0.33	1.56	0.41	5.16	0.85	87.10	3.18	0.38	4.99	87.00	35
3	3	102	5.18	1972	2711	962	0	209	244	60	167	22	1062	0.59	1.85	0.76	3.13	0.80	87.53	3.56	0.73	3.02	87.51	34
Core	CPU	Avg_MHz	Busy%	Bzy_MHz	TSC_MHz	IRQ	SMI	C1	C1E	C3	C6	C7s	C8	C1%	C1E%	C3%	C6%	C7s%	C8%	CPU%c1	CPU%c3	CPU%c6	CPU%c7	CoreTmp	PkgTmp	Totl%C0	Any%C0	GFX%C0	CPUGFX%Pkg%pc2	Pkg%pc3	Pkg%pc6	Pkg%pc7	Pkg%pc8	Pkg%pc9	Pk%pc10	PkgWatt	CorWatt	GFXWattRAMWatt	PKG_%	RAM_%
-	-	258	11.19	2311	2711	4429	0	1774	675	106	637	18	3921	1.01	1.19	0.19	3.39	0.18	82.70	3.25	0.23	3.24	82.09	38	40	46.59	36.17	0.00	0.00	58.70	0.00	0.00	0.00	0.00	0.00	0.00	4.40	3.05	0.00	0.48	0.00	0.00
0	0	487	20.17	2412	2711	773	0	655	341	16	110	1	905	0.59	0.58	0.29	5.23	0.01	72.96	2.15	0.28	5.15	72.25	36	40	46.59	36.17	0.00	0.00	58.70	0.00	0.00	0.00	0.00	0.00	0.00	4.40	3.05	0.00	0.48	0.00	0.00
1	1	375	15.50	2419	2711	1711	0	342	117	36	225	0	1261	1.77	1.27	0.16	4.28	0.00	76.78	4.45	0.14	4.10	75.80	38
2	2	89	4.78	1868	2711	958	0	480	104	20	190	5	919	0.74	0.61	0.13	2.32	0.29	91.05	2.30	0.34	2.02	90.57	35
3	3	83	4.30	1937	2711	987	0	297	113	34	112	12	836	0.95	2.30	0.19	1.75	0.41	90.01	4.12	0.17	1.67	89.75	34

```

---

