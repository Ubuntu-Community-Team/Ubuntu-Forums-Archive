---
title: "Wow! Writing your own program really makes you appreciate the software we get!"
date: 2010-08-17
forum: Programming Talk
---

### Post by Legendary_Bibo on 2010-08-17
Yeah so as I've mentioned before, I've been working on writing a periodic table program complete with a unit converter, and some calculators for simple stuff. Well on the frontend of the UI it looks very simple, but upon coding everything and getting up to about 3,000 or so lines of code (That may be an underestimate), and then having my friends "request" a bunch of extra features (they don't seem to get that what I do for one atomic element I have to do for the other 120 or so elements, they think copy and paste does all the work :confused: ) has made me realized why developers get a little pissed off when people turn around and ***** when the developer doesn't add certain features, or *****es at them until they add features. So to all the hardworking developers who devote your free time to make such awesome programs, thank you! Now back to the grind for me!

---

### Post by Austin25 on 2010-08-17
Well that's good. I'm really happy with what the community has given me, as well. I wwish you good luck on you're project; I hope the compiler doesn't complain too much.;)

---

### Post by Legendary_Bibo on 2010-08-17
It's in Visual Basic on Windows, and then I'm going to port it to Linux through Gambas.

Although VB is being a bad boy right now, it's not outputting text to a label, but I'm sure it's an easy fix, I've just been staring at the code for too long.

---

### Post by Austin25 on 2010-08-17
I'm thinking I might right some apps, but I can't decide what to use: GTK or wxWidgets.

---

### Post by linux18 on 2010-08-17
might want to edit your post, so you won't get a warning/infraction (remove instances of the 'B' word)

---

### Post by juancarlospaco on 2010-08-17
wait, wheres the code?

---

### Post by Legendary_Bibo on 2010-08-17
> **linux18 said:**
> might want to edit your post, so you won't get a warning/infraction (remove instances of the 'B' word)

yeah, I thought it only showed up like that for me. Me thinks the forums' censoring thing isn't working today.

---

### Post by Cuddles McKitten on 2010-08-17
One thing I noticed: if you have to do a lot of additional code for every element, does that mean you're not using objects?  Object-oriented programming helps with exactly that type of scenario.

---

### Post by linux18 on 2010-08-17
you should upload the code and allow some of us to work our magic on it, who knows maybe you'll get the best periodic table ever! mediafire is a great option for uploading

---

### Post by Legendary_Bibo on 2010-08-17
> **juancarlospaco said:**
> wait, wheres the code?

Well I was going to hold off on providing the code until it was done, but here you go. I didn't include the code for the gui, or the resource file, just the forms (what each button does). I didn't include my unit converter because I just started working on that, and my about box isn't all that important.

Periodic Table Main Form:
```

Public Class PTableForm

    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)
        Close()
    End Sub

    Private Sub Label45_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Label45.Click

    End Sub

    Private Sub btnHydrogen_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnHydrogen.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Hydrogen1

        ' For arrays:
        ' ElementAbbreviation{EleAbb,EleName,EleAtomicMass,EleAtomic#,NobleGasElectronConfig,Electronegativity,Atomic Radii,Boiling Point, Freezing Point, Meltin Point, Orbit, Specific Heat Capacity Heat of Vaporization, Covalent Radius?, Heat of Fusion, Electrical Conductivity, Thermal Conductivity, First Ionization Energy, Atomic Volume, State, Protons, Neutrons, Electrons, Density, Year Discovered}

        Dim Hydrogen() As String
        Hydrogen = {"H", "Hydrogen", "1.0079", "1"}

        Dim EleAbb As String = Hydrogen(0)
        lblEAbb.Text = CStr(EleAbb)

        Dim EleName As String = Hydrogen(1)
        lblElementName.Text = CStr(EleName)

        Dim EleAtomicMass As String = Hydrogen(2)
        lblDynamicAMass.Text = CStr(EleAtomicMass)

        Dim EleAtomicNumber As String = Hydrogen(3)
        lblDynamicANumber.Text = CStr(EleAtomicNumber)

    End Sub

    Private Sub btnFrancium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnFrancium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub ElementInfo_Paint(ByVal sender As System.Object, ByVal e As System.Windows.Forms.PaintEventArgs) Handles ElementInfo.Paint

    End Sub

    Private Sub btnRubidium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRubidium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub btnPotassium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPotassium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub btnSodium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSodium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub btnLithium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLithium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub btnCaesium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCaesium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Alkali1
    End Sub

    Private Sub btnRadium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRadium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub PTableForm_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load

    End Sub

    Private Sub btnStrontium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnStrontium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub btnCalcium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCalcium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub btnMagnesium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMagnesium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub btnBeryllium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBeryllium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub btnBarium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBarium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.AlkalineEarthMetal1
    End Sub

    Private Sub btnRadon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRadon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1

    End Sub

    Private Sub btnXenon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnXenon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1
    End Sub

    Private Sub btnKrypton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnKrypton.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1
    End Sub

    Private Sub btnArgon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnArgon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1
    End Sub

    Private Sub btnNeon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNeon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1
    End Sub

    Private Sub btnHelium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnHelium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.NobleGas1
    End Sub

    Private Sub btnAstatine_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnAstatine.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Halogen1
    End Sub

    Private Sub btnChlorine_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnChlorine.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Halogen1
    End Sub

    Private Sub btnBromine_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBromine.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Halogen1
    End Sub

    Private Sub btnIodine_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnIodine.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Halogen1
    End Sub

    Private Sub btnFluorine_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnFluorine.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Halogen1
    End Sub

    Private Sub btnSelenium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSelenium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnSulphur_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSulphur.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnPhosphorus_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPhosphorus.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnCarbon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCarbon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnNitrogen_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNitrogen.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnOxygen_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnOxygen.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Chalcogen1
    End Sub

    Private Sub btnPolonium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPolonium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1

    End Sub

    Private Sub btnBoron_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBoron.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnAntimony_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnAntimony.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnArsenic_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnArsenic.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnGermanium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGermanium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnSilicon_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSilicon.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnTellurium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTellurium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Semimetal1
    End Sub

    Private Sub btnMercury_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMercury.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnThallium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnThallium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnLead_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLead.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnBismuth_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBismuth.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnTin_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTin.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnZinc_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnZinc.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnCadmium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCadmium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnGallium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGallium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnAluminum_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnAluminum.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnIndium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnIndium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.PoorMetal1
    End Sub

    Private Sub btnCopper_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCopper.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnUnunnilium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnUnunnilium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnCobalt_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCobalt.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnIron_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnIron.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnManganese_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnManganese.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnChromium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnChromium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnVanadium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnVanadium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnTitatnium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTitatnium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnScandium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnScandium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnYttrium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnYttrium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnZirconium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnZirconium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnNiobium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNiobium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnMolybdenum_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMolybdenum.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnTechnetium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTechnetium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnRuthenium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRuthenium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnRhodium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRhodium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnPalladium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPalladium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnSilver_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSilver.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnGold_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGold.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnPlatinum_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPlatinum.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnIridium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnIridium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnOsmium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnOsmium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnRhenium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRhenium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnTungsten_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTungsten.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnTantalum_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTantalum.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnHafnium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnHafnium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnRutherfordium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRutherfordium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnDubnium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnDubnium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnSeaborgium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSeaborgium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnBohrium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBohrium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnHassium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnHassium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnMeitnerium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMeitnerium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1
    End Sub

    Private Sub btnNickel_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNickel.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.TransitionMetal1

    End Sub

    Private Sub btnLanthanum_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLanthanum.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnLutetium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLutetium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnYtterbium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnYtterbium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnThulium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnThulium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnErbium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnErbium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnHolmium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnHolmium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnDysprosium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnDysprosium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnTerbium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnTerbium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnGadolinium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGadolinium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnEuropium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnEuropium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnSamarium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSamarium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnPromethium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPromethium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnNeodymium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNeodymium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnPraseodymium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPraseodymium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub btnCerium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCerium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1
    End Sub

    Private Sub Button58_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLanSeries.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Lanthanide1

    End Sub

    Private Sub btnLawrencium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnLawrencium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnNobelium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNobelium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnMendelevium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMendelevium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnFermium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnFermium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnEinsteinium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnEinsteinium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnCalifornium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCalifornium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnBerkelium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnBerkelium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnCurium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCurium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnAmericium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnAmericium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnPlutonium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPlutonium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnNeptunium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnNeptunium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnUranium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnUranium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub Button76_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnActSeries.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnThorium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnThorium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnActinium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnActinium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1
    End Sub

    Private Sub btnProtactinium_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnProtactinium.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Actinide1

    End Sub

    Private Sub btnDefault_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnDefault.Click
        ElementInfo.BackgroundImage = Periodic_Table.My.Resources.Resources.Neutral1
        lblDynamicAMass.Text = ""
        lblDynamicANumber.Text = ""
        lblEAbb.Text = "--"
        lblElementName.Text = ""
    End Sub

    Private Sub btnCalculate_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnCalculate.Click
        Calculate.Visible = True
    End Sub

    Private Sub btnAbout_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnAbout.Click
        AboutBox.Visible = True
    End Sub
End Class

```And the Calculate Form. For some reason I put the Unit Converter on a different form.
```

Public Class Calculate

    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPressureConvert.Click
        Dim Type1 As String
        Dim Type2 As String
        Dim Input As Double


        Type1 = cboP1.Text
        Type2 = cboP2.Text
        Input = FirstBox.Text


        If Type1 = "atm" And Type2 = "atm" Then
            Dim atm1 As Integer
            atm1 = 1
            Dim atm2 As Integer
            atm2 = atm1 * Input

            lblOutput.Text = atm2

        End If

        If Type1 = "Pa" And Type2 = "Pa" Then
            Dim Pa1 As Integer
            Pa1 = 1
            Dim Pa2 As Integer
            Pa2 = Pa1 * Input

            lblOutput.Text = Pa2

        End If

        If Type1 = "torr" And Type2 = "torr" Then
            Dim torr1 As Integer
            torr1 = 1
            Dim torr2 As Integer
            torr2 = torr1 * Input

            lblOutput.Text = torr2

        End If

        If Type1 = "atm" And Type2 = "Pa" Then
            Dim atm As Double
            atm = 90066.5
            Dim Pa As Double
            Pa = atm * Input

            lblOutput.Text = Pa

        End If

        If Type1 = "atm" And Type2 = "torr" Then
            Dim atm As Double
            atm = 760
            Dim torr As Double
            torr = atm * Input

            lblOutput.Text = torr

        End If

        If Type1 = "Pa" And Type2 = "atm" Then
            Dim Pa As Double
            Pa = 0.0000098692
            Dim atm As Double
            atm = Pa * Input

            lblOutput.Text = atm

        End If

        If Type1 = "Pa" And Type2 = "torr" Then
            Dim Pa As Double
            Pa = 0.0075006
            Dim torr As Double
            torr = Input * Pa

            lblOutput.Text = torr

        End If

        If Type1 = "torr" And Type2 = "atm" Then
            Dim torr As Double
            torr = 0.0013158
            Dim atm As Double
            atm = torr * Input

            lblOutput.Text = atm

        End If

        If Type1 = "torr" And Type2 = "Pa" Then
            Dim torr As Double
            torr = 133.322
            Dim Pa As Double
            Pa = torr * Input

            lblOutput.Text = Pa

        End If
    End Sub

    Private Sub Calculate_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load

    End Sub

    Private Sub btnClear_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnClear.Click
        lblOutput.Text = ""
        FirstBox.Text = ""
    End Sub

    Private Sub btnGasClear_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGasClear.Click
        GasP.Text = 0
        GasT.Text = 0
        GasN.Text = 0
        GasV.Text = 0
    End Sub

    Private Sub btnGasCalculate_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnGasCalculate.Click
        Dim P As Double
        Dim V As Double
        Dim N As Double
        Dim R As Double
        Dim T As Double

        P = GasP.Text
        V = GasV.Text
        N = GasN.Text
        T = GasT.Text
        R = 0.08206

        If P = 0 Then
            P = (N * R * T) / V
            GasP.Text = P
        End If

        If V = 0 Then
            V = (N * R * T) / P
            GasV.Text = V
        End If

        If N = 0 Then
            N = (P * V) / (R * T)
            GasN.Text = N
        End If

        If T = 0 Then
            T = (P * V) / (N * R)
            GasT.Text = T
        End If
    End Sub

    Private Sub GasP_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles GasP.Click
        GasP.Text = ""

    End Sub

    Private Sub GasN_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles GasN.Click
        GasN.Text = ""

    End Sub

    Private Sub GasV_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles GasV.Click
        GasV.Text = ""

    End Sub

    Private Sub GasT_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles GasT.Click
        GasT.Text = ""

    End Sub

    Private Sub Button1_Click_1(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
        UnitConversion.Visible = True

    End Sub

    Private Sub rBtnGramsToMoles_CheckedChanged(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles rBtnGramsToMoles.CheckedChanged


    End Sub

    Private Sub rBtnMolesToGrams_CheckedChanged(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles rBtnMolesToGrams.CheckedChanged


    End Sub

    Private Sub btnMoleClear_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMoleClear.Click
        Amount.Text = ""
        cboElementList.Text = ""
        lblEquals.Text = ""
        lblMolesOrGrams.Text = ""
        Label12.Text = ""
        rBtnMolesToGrams.Checked = True
        rBtnGramsToMoles.Checked = False
    End Sub

    Private Sub btnMoleConvert_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnMoleConvert.Click

        If rBtnMolesToGrams.Checked = True Then

            Dim InputConvert As Double
            InputConvert = Amount.Text

            Dim ElementType As String
            ElementType = cboElementList.Text

            If ElementType = "Ac Actinium" Then
                Dim Ac As Double
                Ac = 227.028
                Dim Output As Double
                Output = InputConvert * Ac
                lblEquals.Text = Output
            End If

            If ElementType = "Al Aluminum" Then
                Dim Al As Double
                Al = 23.982
                Dim Output As Double
                Output = InputConvert * Al
                lblEquals.Text = Output
            End If

            If ElementType = "Am Americium" Then
                Dim Am As Double
                Am = 243
                Dim Output As Double
                Output = InputConvert * Am
                lblEquals.Text = Output
            End If

            If ElementType = "Sb Antimony" Then
                Dim Sb As Double
                Sb = 121.757
                Dim Output As Double
                Output = InputConvert * Sb
                lblEquals.Text = Output
            End If

            If ElementType = "Ar Argon" Then
                Dim Ar As Double
                Ar = 39.948
                Dim Output As Double
                Output = InputConvert * Ar
                lblEquals.Text = Output
            End If

            If ElementType = "As Arsenic" Then
                Dim Arsenic As Double
                Arsenic = 74.922
                Dim Output As Double
                Output = InputConvert * Arsenic
                lblEquals.Text = Output
            End If

            If ElementType = "At Astatine" Then
                Dim At As Double
                At = 210
                Dim Output As Double
                Output = InputConvert * At
                lblEquals.Text = Output
            End If

            If ElementType = "Ba Barium" Then
                Dim Ba As Double
                Ba = 137.327
                Dim Output As Double
                Output = InputConvert * Ba
                lblEquals.Text = Output
            End If

            If ElementType = "Bk Berkelium" Then
                Dim Bk As Double
                Bk = 247
                Dim Output As Double
                Output = InputConvert * Bk
                lblEquals.Text = Output
            End If

            If ElementType = "Be Beryllium" Then
                Dim Be As Double
                Be = 9.012
                Dim Output As Double
                Output = InputConvert * Be
                lblEquals.Text = Output
            End If

            If ElementType = "Bi Bismuth" Then
                Dim Bi As Double
                Bi = 208.98
                Dim Output As Double
                Output = InputConvert * Bi
                lblEquals.Text = Output
            End If

            If ElementType = "Bh Bohrium" Then
                Dim Bh As Double
                Bh = 262
                Dim Output As Double
                Output = InputConvert * Bh
                lblEquals.Text = Output
            End If

            If ElementType = "B Boron" Then
                Dim B As Double
                B = 10.811
                Dim Output As Double
                Output = InputConvert * B
                lblEquals.Text = Output
            End If

            If ElementType = "Br Bromine" Then
                Dim Br As Double
                Br = 79.904
                Dim Output As Double
                Output = InputConvert * Br
                lblEquals.Text = Output
            End If

            If ElementType = "Cd Cadmium" Then
                Dim Cd As Double
                Cd = 112.411
                Dim Output As Double
                Output = InputConvert * Cd
                lblEquals.Text = Output
            End If

            If ElementType = "Ca Calcium" Then
                Dim Ca As Double
                Ca = 40.078
                Dim Output As Double
                Output = InputConvert * Ca
                lblEquals.Text = Output
            End If

            If ElementType = "Cf Californium" Then
                Dim Cf As Double
                Cf = 251
                Dim Output As Double
                Output = InputConvert * Cf
                lblEquals.Text = Output
            End If

            If ElementType = "C Carbon" Then
                Dim C As Double
                C = 12.011
                Dim Output As Double
                Output = InputConvert * C
                lblEquals.Text = Output
            End If

            If ElementType = "Ce Cerium" Then
                Dim Ce As Double
                Ce = 140.115
                Dim Output As Double
                Output = InputConvert * Ce
                lblEquals.Text = Output
            End If

            If ElementType = "Cr Chromium" Then
                Dim Cr As Double
                Cr = 51.9961
                Dim Output As Double
                Output = InputConvert * Cr
                lblEquals.Text = Output
            End If

            If ElementType = "Cs Cesium" Then
                Dim Cs As Double
                Cs = 132.9054
                Dim Output As Double
                Output = InputConvert * Cs
                lblEquals.Text = Output
            End If

            If ElementType = "Cl Chlorine" Then
                Dim Cl As Double
                Cl = 51.9961
                Dim Output As Double
                Output = InputConvert * Cl
                lblEquals.Text = Output
            End If

            If ElementType = "Co Cobalt" Then
                Dim Co As Double
                Co = 58.9332
                Dim Output As Double
                Output = InputConvert * Co
                lblEquals.Text = Output
            End If

            If ElementType = "Cu Copper" Then
                Dim Cu As Double
                Cu = 63.546
                Dim Output As Double
                Output = InputConvert * Cu
                lblEquals.Text = Output
            End If

            If ElementType = "Cm Curium" Then
                Dim Cm As Double
                Cm = 247
                Dim Output As Double
                Output = InputConvert * Cm
                lblEquals.Text = Output
            End If

            If ElementType = "Db Dubnium" Then
                Dim Db As Double
                Db = 262
                Dim Output As Double
                Output = InputConvert * Db
                lblEquals.Text = Output
            End If

            If ElementType = "Dy Dysprosium" Then
                Dim Dy As Double
                Dy = 162.503
                Dim Output As Double
                Output = InputConvert * Dy
                lblEquals.Text = Output
            End If

            If ElementType = "Es Einsteinium" Then
                Dim Es As Double
                Es = 252
                Dim Output As Double
                Output = InputConvert * Es
                lblEquals.Text = Output
            End If

            If ElementType = "Er Erbium" Then
                Dim Er As Double
                Er = 167.263
                Dim Output As Double
                Output = InputConvert * Er
                lblEquals.Text = Output
            End If

            If ElementType = "Eu Europium" Then
                Dim Eu As Double
                Eu = 151.965
                Dim Output As Double
                Output = InputConvert * Eu
                lblEquals.Text = Output
            End If

            If ElementType = "Fm Fermium" Then
                Dim Fm As Double
                Fm = 257
                Dim Output As Double
                Output = InputConvert * Fm
                lblEquals.Text = Output
            End If

            If ElementType = "F Fluorine" Then
                Dim F As Double
                F = 18.9984
                Dim Output As Double
                Output = InputConvert * F
                lblEquals.Text = Output
            End If

            If ElementType = "Fr Francium" Then
                Dim Fr As Double
                Fr = 223
                Dim Output As Double
                Output = InputConvert * Fr
                lblEquals.Text = Output
            End If

            If ElementType = "Gd Gadolinium" Then
                Dim Gd As Double
                Gd = 157.253
                Dim Output As Double
                Output = InputConvert * Gd
                lblEquals.Text = Output
            End If

            If ElementType = "Ga Gallium" Then
                Dim Ga As Double
                Ga = 69.723
                Dim Output As Double
                Output = InputConvert * Ga
                lblEquals.Text = Output
            End If

            If ElementType = "Ge Germanium" Then
                Dim Ge As Double
                Ge = 72.61
                Dim Output As Double
                Output = InputConvert * Ge
                lblEquals.Text = Output
            End If

            If ElementType = "Au Gold" Then
                Dim Au As Double
                Au = 196.96654
                Dim Output As Double
                Output = InputConvert * Au
                lblEquals.Text = Output
            End If

            If ElementType = "Hf Hafnium" Then
                Dim Hf As Double
                Hf = 178.492
                Dim Output As Double
                Output = InputConvert * Hf
                lblEquals.Text = Output
            End If

            If ElementType = "Hs Hassium" Then
                Dim Hs As Double
                Hs = 265
                Dim Output As Double
                Output = InputConvert * Hs
                lblEquals.Text = Output
            End If

            If ElementType = "He Helium" Then
                Dim He As Double
                He = 4.002602
                Dim Output As Double
                Output = InputConvert * He
                lblEquals.Text = Output
            End If

            If ElementType = "Ho Holmium" Then
                Dim Ho As Double
                Ho = 164.93032
                Dim Output As Double
                Output = InputConvert * Ho
                lblEquals.Text = Output
            End If

            If ElementType = "H Hydrogen" Then
                Dim H As Double
                H = 1.0079
                Dim Output As Double
                Output = InputConvert * H
                lblEquals.Text = Output
            End If

            If ElementType = "In Indium" Then
                Dim Indium As Double
                Indium = 114.82
                Dim Output As Double
                Output = InputConvert * Indium
                lblEquals.Text = Output
            End If

            If ElementType = "I Iodine" Then
                Dim I As Double
                I = 126.90447
                Dim Output As Double
                Output = InputConvert * I
                lblEquals.Text = Output
            End If

            If ElementType = "Ir Iridium" Then
                Dim Ir As Double
                Ir = 192.223
                Dim Output As Double
                Output = InputConvert * Ir
                lblEquals.Text = Output
            End If

            If ElementType = "Fe Iron" Then
                Dim Fe As Double
                Fe = 55.847
                Dim Output As Double
                Output = InputConvert * Fe
                lblEquals.Text = Output
            End If

            If ElementType = "Kr Krypton" Then
                Dim Kr As Double
                Kr = 83.801
                Dim Output As Double
                Output = InputConvert * Kr
                lblEquals.Text = Output
            End If

            If ElementType = "La Lanthanum" Then
                Dim La As Double
                La = 138.9055
                Dim Output As Double
                Output = InputConvert * La
                lblEquals.Text = Output
            End If

            If ElementType = "Lr Lawrencium" Then
                Dim Lr As Double
                Lr = 262
                Dim Output As Double
                Output = InputConvert * Lr
                lblEquals.Text = Output
            End If

            If ElementType = "Pb Lead" Then
                Dim Pb As Double
                Pb = 207.21
                Dim Output As Double
                Output = InputConvert * Pb
                lblEquals.Text = Output
            End If

            If ElementType = "Li Lithium" Then
                Dim Li As Double
                Li = 6.941
                Dim Output As Double
                Output = InputConvert * Li
                lblEquals.Text = Output
            End If

            If ElementType = "Lu Lutetium" Then
                Dim Lu As Double
                Lu = 174.967
                Dim Output As Double
                Output = InputConvert * Lu
                lblEquals.Text = Output
            End If

            If ElementType = "Mg Magnesium" Then
                Dim Mg As Double
                Mg = 24.305
                Dim Output As Double
                Output = InputConvert * Mg
                lblEquals.Text = Output
            End If

            If ElementType = "Mn Manganese" Then
                Dim Mn As Double
                Mn = 54.938
                Dim Output As Double
                Output = InputConvert * Mn
                lblEquals.Text = Output
            End If

            If ElementType = "Mt Meiterium" Then
                Dim Mt As Double
                Mt = 266
                Dim Output As Double
                Output = InputConvert * Mt
                lblEquals.Text = Output
            End If

            If ElementType = "Md Mendelevium" Then
                Dim Md As Double
                Md = 258
                Dim Output As Double
                Output = InputConvert * Md
                lblEquals.Text = Output
            End If

            If ElementType = "Hg Mercury" Then
                Dim Hg As Double
                Hg = 200.593
                Dim Output As Double
                Output = InputConvert * Hg
                lblEquals.Text = Output
            End If

            If ElementType = "Mo Molybdenum" Then
                Dim Mo As Double
                Mo = 95.941
                Dim Output As Double
                Output = InputConvert * Mo
                lblEquals.Text = Output
            End If

            If ElementType = "Nd Neodymium" Then
                Dim Nd As Double
                Nd = 144.24
                Dim Output As Double
                Output = InputConvert * Nd
                lblEquals.Text = Output
            End If

            If ElementType = "Ne Neon" Then
                Dim Ne As Double
                Ne = 20.1797
                Dim Output As Double
                Output = InputConvert * Ne
                lblEquals.Text = Output
            End If

            If ElementType = "Np Neptunium" Then
                Dim Np As Double
                Np = 237.048
                Dim Output As Double
                Output = InputConvert * Np
                lblEquals.Text = Output
            End If

            If ElementType = "Ni Nickel" Then
                Dim Ni As Double
                Ni = 58.6934
                Dim Output As Double
                Output = InputConvert * Ni
                lblEquals.Text = Output
            End If

            If ElementType = "Nb Niobium" Then
                Dim Nb As Double
                Nb = 92.90638
                Dim Output As Double
                Output = InputConvert * Nb
                lblEquals.Text = Output
            End If

            If ElementType = "N Nitrogen" Then
                Dim N As Double
                N = 14.00674
                Dim Output As Double
                Output = InputConvert * N
                lblEquals.Text = Output
            End If

            If ElementType = "No Nobelium" Then
                Dim No As Double
                No = 259
                Dim Output As Double
                Output = InputConvert * No
                lblEquals.Text = Output
            End If

            If ElementType = "Os Osmium" Then
                Dim Os As Double
                Os = 190.21
                Dim Output As Double
                Output = InputConvert * Os
                lblEquals.Text = Output
            End If

            If ElementType = "O Oxygen" Then
                Dim O As Double
                O = 15.9994
                Dim Output As Double
                Output = InputConvert * O
                lblEquals.Text = Output
            End If

            If ElementType = "Pd Palladium" Then
                Dim Pd As Double
                Pd = 106.421
                Dim Output As Double
                Output = InputConvert * Pd
                lblEquals.Text = Output
            End If

            If ElementType = "P Phosphorus" Then
                Dim P As Double
                P = 30.9737624
                Dim Output As Double
                Output = InputConvert * P
                lblEquals.Text = Output
            End If

            If ElementType = "Pt Platinum" Then
                Dim Pt As Double
                Pt = 195.083
                Dim Output As Double
                Output = InputConvert * Pt
                lblEquals.Text = Output
            End If

            If ElementType = "Pu Plutonium" Then
                Dim Pu As Double
                Pu = 244
                Dim Output As Double
                Output = InputConvert * Pu
                lblEquals.Text = Output
            End If

            If ElementType = "Po Polonium" Then
                Dim Po As Double
                Po = 209
                Dim Output As Double
                Output = InputConvert * Po
                lblEquals.Text = Output
            End If

            If ElementType = "K Potassium" Then
                Dim K As Double
                K = 39.0983
                Dim Output As Double
                Output = InputConvert * K
                lblEquals.Text = Output
            End If

            If ElementType = "Pr Praseodymium" Then
                Dim Pr As Double
                Pr = 140.907653
                Dim Output As Double
                Output = InputConvert * Pr
                lblEquals.Text = Output
            End If

            If ElementType = "Pm Promethium" Then
                Dim Pm As Double
                Pm = 145
                Dim Output As Double
                Output = InputConvert * Pm
                lblEquals.Text = Output
            End If

            If ElementType = "Pa Protactinium" Then
                Dim Pa As Double
                Pa = 231.0359
                Dim Output As Double
                Output = InputConvert * Pa
                lblEquals.Text = Output
            End If

            If ElementType = "Ra Radium" Then
                Dim Ra As Double
                Ra = 226.025
                Dim Output As Double
                Output = InputConvert * Ra
                lblEquals.Text = Output
            End If

            If ElementType = "Rn Radon" Then
                Dim Rn As Double
                Rn = 222
                Dim Output As Double
                Output = InputConvert * Rn
                lblEquals.Text = Output
            End If

            If ElementType = "Re Rhenium" Then
                Dim Re As Double
                Re = 186.2071
                Dim Output As Double
                Output = InputConvert * Re
                lblEquals.Text = Output
            End If

            If ElementType = "Rh Rhodium" Then
                Dim Rh As Double
                Rh = 102.9055
                Dim Output As Double
                Output = InputConvert * Rh
                lblEquals.Text = Output
            End If

            If ElementType = "Rb Rubidium" Then
                Dim Rb As Double
                Rb = 85.4678
                Dim Output As Double
                Output = InputConvert * Rb
                lblEquals.Text = Output
            End If

            If ElementType = "Ru Ruthenium" Then
                Dim Ru As Double
                Ru = 101.07
                Dim Output As Double
                Output = InputConvert * Ru
                lblEquals.Text = Output
            End If

            If ElementType = "Rf Rutherfordium" Then
                Dim Rf As Double
                Rf = 261
                Dim Output As Double
                Output = InputConvert * Rf
                lblEquals.Text = Output
            End If

            If ElementType = "Sm Samarium" Then
                Dim Sm As Double
                Sm = 150.36
                Dim Output As Double
                Output = InputConvert * Sm
                lblEquals.Text = Output
            End If

            If ElementType = "Sc Scandium" Then
                Dim Sc As Double
                Sc = 44.95591
                Dim Output As Double
                Output = InputConvert * Sc
                lblEquals.Text = Output
            End If

            If ElementType = "Sg Seaborgium" Then
                Dim Sg As Double
                Sg = 263
                Dim Output As Double
                Output = InputConvert * Sg
                lblEquals.Text = Output
            End If

            If ElementType = "Se Selenium" Then
                Dim Se As Double
                Se = 78.96
                Dim Output As Double
                Output = InputConvert * Se
                lblEquals.Text = Output
            End If

            If ElementType = "Si Silicon" Then
                Dim Si As Double
                Si = 28.0855
                Dim Output As Double
                Output = InputConvert * Si
                lblEquals.Text = Output
            End If

            If ElementType = "Ag Silver" Then
                Dim Ag As Double
                Ag = 107.8682
                Dim Output As Double
                Output = InputConvert * Ag
                lblEquals.Text = Output
            End If

            If ElementType = "Na Sodium" Then
                Dim Na As Double
                Na = 22.989768
                Dim Output As Double
                Output = InputConvert * Na
                lblEquals.Text = Output
            End If

            If ElementType = "Sr Strontium" Then
                Dim Sr As Double
                Sr = 87.62
                Dim Output As Double
                Output = InputConvert * Sr
                lblEquals.Text = Output
            End If

            If ElementType = "S Sulphur" Then
                Dim S As Double
                S = 32.066
                Dim Output As Double
                Output = InputConvert * S
                lblEquals.Text = Output
            End If

            If ElementType = "Ta Tantalum" Then
                Dim Ta As Double
                Ta = 180.9479
                Dim Output As Double
                Output = InputConvert * Ta
                lblEquals.Text = Output
            End If

            If ElementType = "Tc Technetium" Then
                Dim Tc As Double
                Tc = 98
                Dim Output As Double
                Output = InputConvert * Tc
                lblEquals.Text = Output
            End If

            If ElementType = "Te Tellurium" Then
                Dim Te As Double
                Te = 127.603
                Dim Output As Double
                Output = InputConvert * Te
                lblEquals.Text = Output
            End If

            If ElementType = "Tb Terbium" Then
                Dim Tb As Double
                Tb = 158.92534
                Dim Output As Double
                Output = InputConvert * Tb
                lblEquals.Text = Output
            End If

            If ElementType = "Tl Thallium" Then
                Dim Tl As Double
                Tl = 204.3833
                Dim Output As Double
                Output = InputConvert * Tl
                lblEquals.Text = Output
            End If

            If ElementType = "Th Thorium" Then
                Dim Th As Double
                Th = 232.0381
                Dim Output As Double
                Output = InputConvert * Th
                lblEquals.Text = Output
            End If

            If ElementType = "Tm Thulium" Then
                Dim Tm As Double
                Tm = 168.93421
                Dim Output As Double
                Output = InputConvert * Tm
                lblEquals.Text = Output
            End If

            If ElementType = "Sn Tin" Then
                Dim Sn As Double
                Sn = 118.71
                Dim Output As Double
                Output = InputConvert * Sn
                lblEquals.Text = Output
            End If

            If ElementType = "Ti Titanium" Then
                Dim Ti As Double
                Ti = 47.88
                Dim Output As Double
                Output = InputConvert * Ti
                lblEquals.Text = Output
            End If

            If ElementType = "W Tungsten" Then
                Dim W As Double
                W = 183.85
                Dim Output As Double
                Output = InputConvert * W
                lblEquals.Text = Output
            End If

            If ElementType = "U Uranium" Then
                Dim U As Double
                U = 238.0289
                Dim Output As Double
                Output = InputConvert * U
                lblEquals.Text = Output
            End If

            If ElementType = "V Vanadium" Then
                Dim V As Double
                V = 50.9415
                Dim Output As Double
                Output = InputConvert * V
                lblEquals.Text = Output
            End If

            If ElementType = "Xe Xenon" Then
                Dim Xe As Double
                Xe = 131.29
                Dim Output As Double
                Output = InputConvert * Xe
                lblEquals.Text = Output
            End If

            If ElementType = "Yb Ytterbium" Then
                Dim Yb As Double
                Yb = 173.04
                Dim Output As Double
                Output = InputConvert * Yb
                lblEquals.Text = Output
            End If

            If ElementType = "Y Yttrium" Then
                Dim Y As Double
                Y = 88.90585
                Dim Output As Double
                Output = InputConvert * Y
                lblEquals.Text = Output
            End If

            If ElementType = "Zn Zinc" Then
                Dim Zn As Double
                Zn = 65.39
                Dim Output As Double
                Output = InputConvert * Zn
                lblEquals.Text = Output
            End If

            If ElementType = "Zr Zirconium" Then
                Dim Zr As Double
                Zr = 91.224
                Dim Output As Double
                Output = InputConvert * Zr
                lblEquals.Text = Output
            End If

            'And now for something completely different!
            'These are the synthetic radioactive triple lettered elements. Some were also given actual
            'names which I've included as well

            'I used the masses of the most stable isotopes

            If ElementType = "Uub Ununbium" Then
                Dim Uub As Double
                Uub = 285
                Dim Output As Double
                Output = InputConvert * Uub
                lblEquals.Text = Output
            End If

            If ElementType = "Cn Copernicium" Then
                Dim Cn As Double
                Cn = 285
                Dim Output As Double
                Output = InputConvert * Cn
                lblEquals.Text = Output
            End If

            If ElementType = "Uuh Ununhexium" Then
                Dim Uuh As Double
                Uuh = 293
                Dim Output As Double
                Output = InputConvert * Uuh
                lblEquals.Text = Output
            End If

            If ElementType = "Uun Ununnilium" Then
                Dim Uun As Double
                Uun = 281
                Dim Output As Double
                Output = InputConvert * Uun
                lblEquals.Text = Output
            End If

            If ElementType = "Ds Darmstadtium" Then
                Dim Ds As Double
                Ds = 281
                Dim Output As Double
                Output = InputConvert * Ds
                lblEquals.Text = Output
            End If

            If ElementType = "Uuo Ununoctium" Then
                Dim Uuo As Double
                Uuo = 294
                Dim Output As Double
                Output = InputConvert * Uuo
                lblEquals.Text = Output
            End If

            If ElementType = "Uup Ununpentium" Then
                Dim Uup As Double
                Uup = 289
                Dim Output As Double
                Output = InputConvert * Uup
                lblEquals.Text = Output
            End If

            If ElementType = "Uuq Ununquadium" Then
                Dim Uuq As Double
                Uuq = 289
                Dim Output As Double
                Output = InputConvert * Uuq
                lblEquals.Text = Output
            End If

            If ElementType = "Uus Ununseptium" Then
                Dim Uus As Double
                Uus = 294
                Dim Output As Double
                Output = InputConvert * Uus
                lblEquals.Text = Output
            End If

            If ElementType = "Uut Ununtrium" Then
                Dim Uut As Double
                Uut = 286
                Dim Output As Double
                Output = InputConvert * Uut
                lblEquals.Text = Output
            End If

            If ElementType = "Uuu Ununumium" Then
                Dim Uuu As Double
                Uuu = 281
                Dim Output As Double
                Output = InputConvert * Uuu
                lblEquals.Text = Output
            End If

            If ElementType = "Rg Roentgenium" Then
                Dim Rg As Double
                Rg = 281
                Dim Output As Double
                Output = InputConvert * Rg
                lblEquals.Text = Output
            End If

            Label12.Text = "grams"
        End If

        If rBtnGramsToMoles.Checked = True Then
            Dim InputConvert As Double
            InputConvert = Amount.Text

            Dim ElementType As String
            ElementType = cboElementList.Text

            If ElementType = "Ac Actinium" Then
                Dim Ac As Double
                Ac = 227.028
                Dim Output As Double
                Output = InputConvert / Ac
                lblEquals.Text = Output
            End If

            If ElementType = "Al Aluminum" Then
                Dim Al As Double
                Al = 23.982
                Dim Output As Double
                Output = InputConvert / Al
                lblEquals.Text = Output
            End If

            If ElementType = "Am Americium" Then
                Dim Am As Double
                Am = 243
                Dim Output As Double
                Output = InputConvert / Am
                lblEquals.Text = Output
            End If

            If ElementType = "Sb Antimony" Then
                Dim Sb As Double
                Sb = 121.757
                Dim Output As Double
                Output = InputConvert / Sb
                lblEquals.Text = Output
            End If

            If ElementType = "Ar Argon" Then
                Dim Ar As Double
                Ar = 39.948
                Dim Output As Double
                Output = InputConvert / Ar
                lblEquals.Text = Output
            End If

            If ElementType = "As Arsenic" Then
                Dim Arsenic As Double
                Arsenic = 74.922
                Dim Output As Double
                Output = InputConvert / Arsenic
                lblEquals.Text = Output
            End If

            If ElementType = "At Astatine" Then
                Dim At As Double
                At = 210
                Dim Output As Double
                Output = InputConvert / At
                lblEquals.Text = Output
            End If

            If ElementType = "Ba Barium" Then
                Dim Ba As Double
                Ba = 137.327
                Dim Output As Double
                Output = InputConvert / Ba
                lblEquals.Text = Output
            End If

            If ElementType = "Bk Berkelium" Then
                Dim Bk As Double
                Bk = 247
                Dim Output As Double
                Output = InputConvert / Bk
                lblEquals.Text = Output
            End If

            If ElementType = "Be Beryllium" Then
                Dim Be As Double
                Be = 9.012
                Dim Output As Double
                Output = InputConvert / Be
                lblEquals.Text = Output
            End If

            If ElementType = "Bi Bismuth" Then
                Dim Bi As Double
                Bi = 208.98
                Dim Output As Double
                Output = InputConvert / Bi
                lblEquals.Text = Output
            End If

            If ElementType = "Bh Bohrium" Then
                Dim Bh As Double
                Bh = 262
                Dim Output As Double
                Output = InputConvert / Bh
                lblEquals.Text = Output
            End If

            If ElementType = "B Boron" Then
                Dim B As Double
                B = 10.811
                Dim Output As Double
                Output = InputConvert / B
                lblEquals.Text = Output
            End If

            If ElementType = "Br Bromine" Then
                Dim Br As Double
                Br = 79.904
                Dim Output As Double
                Output = InputConvert / Br
                lblEquals.Text = Output
            End If

            If ElementType = "Cd Cadmium" Then
                Dim Cd As Double
                Cd = 112.411
                Dim Output As Double
                Output = InputConvert / Cd
                lblEquals.Text = Output
            End If

            If ElementType = "Ca Calcium" Then
                Dim Ca As Double
                Ca = 40.078
                Dim Output As Double
                Output = InputConvert / Ca
                lblEquals.Text = Output
            End If

            If ElementType = "Cf Californium" Then
                Dim Cf As Double
                Cf = 251
                Dim Output As Double
                Output = InputConvert / Cf
                lblEquals.Text = Output
            End If

            If ElementType = "C Carbon" Then
                Dim C As Double
                C = 12.011
                Dim Output As Double
                Output = InputConvert / C
                lblEquals.Text = Output
            End If

            If ElementType = "Ce Cerium" Then
                Dim Ce As Double
                Ce = 140.115
                Dim Output As Double
                Output = InputConvert / Ce
                lblEquals.Text = Output
            End If

            If ElementType = "Cr Chromium" Then
                Dim Cr As Double
                Cr = 51.9961
                Dim Output As Double
                Output = InputConvert / Cr
                lblEquals.Text = Output
            End If

            If ElementType = "Cs Cesium" Then
                Dim Cs As Double
                Cs = 132.9054
                Dim Output As Double
                Output = InputConvert / Cs
                lblEquals.Text = Output
            End If

            If ElementType = "Cl Chlorine" Then
                Dim Cl As Double
                Cl = 51.9961
                Dim Output As Double
                Output = InputConvert / Cl
                lblEquals.Text = Output
            End If

            If ElementType = "Co Cobalt" Then
                Dim Co As Double
                Co = 58.9332
                Dim Output As Double
                Output = InputConvert / Co
                lblEquals.Text = Output
            End If

            If ElementType = "Cu Copper" Then
                Dim Cu As Double
                Cu = 63.546
                Dim Output As Double
                Output = InputConvert / Cu
                lblEquals.Text = Output
            End If

            If ElementType = "Cm Curium" Then
                Dim Cm As Double
                Cm = 247
                Dim Output As Double
                Output = InputConvert / Cm
                lblEquals.Text = Output
            End If

            If ElementType = "Db Dubnium" Then
                Dim Db As Double
                Db = 262
                Dim Output As Double
                Output = InputConvert / Db
                lblEquals.Text = Output
            End If

            If ElementType = "Dy Dysprosium" Then
                Dim Dy As Double
                Dy = 162.503
                Dim Output As Double
                Output = InputConvert / Dy
                lblEquals.Text = Output
            End If

            If ElementType = "Es Einsteinium" Then
                Dim Es As Double
                Es = 252
                Dim Output As Double
                Output = InputConvert / Es
                lblEquals.Text = Output
            End If

            If ElementType = "Er Erbium" Then
                Dim Er As Double
                Er = 167.263
                Dim Output As Double
                Output = InputConvert / Er
                lblEquals.Text = Output
            End If

            If ElementType = "Eu Europium" Then
                Dim Eu As Double
                Eu = 151.965
                Dim Output As Double
                Output = InputConvert / Eu
                lblEquals.Text = Output
            End If

            If ElementType = "Fm Fermium" Then
                Dim Fm As Double
                Fm = 257
                Dim Output As Double
                Output = InputConvert / Fm
                lblEquals.Text = Output
            End If

            If ElementType = "F Fluorine" Then
                Dim F As Double
                F = 18.9984
                Dim Output As Double
                Output = InputConvert / F
                lblEquals.Text = Output
            End If

            If ElementType = "Fr Francium" Then
                Dim Fr As Double
                Fr = 223
                Dim Output As Double
                Output = InputConvert / Fr
                lblEquals.Text = Output
            End If

            If ElementType = "Gd Gadolinium" Then
                Dim Gd As Double
                Gd = 157.253
                Dim Output As Double
                Output = InputConvert / Gd
                lblEquals.Text = Output
            End If

            If ElementType = "Ga Gallium" Then
                Dim Ga As Double
                Ga = 69.723
                Dim Output As Double
                Output = InputConvert / Ga
                lblEquals.Text = Output
            End If

            If ElementType = "Ge Germanium" Then
                Dim Ge As Double
                Ge = 72.61
                Dim Output As Double
                Output = InputConvert / Ge
                lblEquals.Text = Output
            End If

            If ElementType = "Au Gold" Then
                Dim Au As Double
                Au = 196.96654
                Dim Output As Double
                Output = InputConvert / Au
                lblEquals.Text = Output
            End If

            If ElementType = "Hf Hafnium" Then
                Dim Hf As Double
                Hf = 178.492
                Dim Output As Double
                Output = InputConvert / Hf
                lblEquals.Text = Output
            End If

            If ElementType = "Hs Hassium" Then
                Dim Hs As Double
                Hs = 265
                Dim Output As Double
                Output = InputConvert / Hs
                lblEquals.Text = Output
            End If

            If ElementType = "He Helium" Then
                Dim He As Double
                He = 4.002602
                Dim Output As Double
                Output = InputConvert / He
                lblEquals.Text = Output
            End If

            If ElementType = "Ho Holmium" Then
                Dim Ho As Double
                Ho = 164.93032
                Dim Output As Double
                Output = InputConvert / Ho
                lblEquals.Text = Output
            End If

            If ElementType = "H Hydrogen" Then
                Dim H As Double
                H = 1.0079
                Dim Output As Double
                Output = InputConvert / H
                lblEquals.Text = Output
            End If

            If ElementType = "In Indium" Then
                Dim Indium As Double
                Indium = 114.82
                Dim Output As Double
                Output = InputConvert / Indium
                lblEquals.Text = Output
            End If

            If ElementType = "I Iodine" Then
                Dim I As Double
                I = 126.90447
                Dim Output As Double
                Output = InputConvert / I
                lblEquals.Text = Output
            End If

            If ElementType = "Ir Iridium" Then
                Dim Ir As Double
                Ir = 192.223
                Dim Output As Double
                Output = InputConvert / Ir
                lblEquals.Text = Output
            End If

            If ElementType = "Fe Iron" Then
                Dim Fe As Double
                Fe = 55.847
                Dim Output As Double
                Output = InputConvert / Fe
                lblEquals.Text = Output
            End If

            If ElementType = "Kr Krypton" Then
                Dim Kr As Double
                Kr = 83.801
                Dim Output As Double
                Output = InputConvert / Kr
                lblEquals.Text = Output
            End If

            If ElementType = "La Lanthanum" Then
                Dim La As Double
                La = 138.9055
                Dim Output As Double
                Output = InputConvert / La
                lblEquals.Text = Output
            End If

            If ElementType = "Lr Lawrencium" Then
                Dim Lr As Double
                Lr = 262
                Dim Output As Double
                Output = InputConvert / Lr
                lblEquals.Text = Output
            End If

            If ElementType = "Pb Lead" Then
                Dim Pb As Double
                Pb = 207.21
                Dim Output As Double
                Output = InputConvert / Pb
                lblEquals.Text = Output
            End If

            If ElementType = "Li Lithium" Then
                Dim Li As Double
                Li = 6.941
                Dim Output As Double
                Output = InputConvert / Li
                lblEquals.Text = Output
            End If

            If ElementType = "Lu Lutetium" Then
                Dim Lu As Double
                Lu = 174.967
                Dim Output As Double
                Output = InputConvert / Lu
                lblEquals.Text = Output
            End If

            If ElementType = "Mg Magnesium" Then
                Dim Mg As Double
                Mg = 24.305
                Dim Output As Double
                Output = InputConvert / Mg
                lblEquals.Text = Output
            End If

            If ElementType = "Mn Manganese" Then
                Dim Mn As Double
                Mn = 54.938
                Dim Output As Double
                Output = InputConvert / Mn
                lblEquals.Text = Output
            End If

            If ElementType = "Mt Meiterium" Then
                Dim Mt As Double
                Mt = 266
                Dim Output As Double
                Output = InputConvert / Mt
                lblEquals.Text = Output
            End If

            If ElementType = "Md Mendelevium" Then
                Dim Md As Double
                Md = 258
                Dim Output As Double
                Output = InputConvert / Md
                lblEquals.Text = Output
            End If

            If ElementType = "Hg Mercury" Then
                Dim Hg As Double
                Hg = 200.593
                Dim Output As Double
                Output = InputConvert / Hg
                lblEquals.Text = Output
            End If

            If ElementType = "Mo Molybdenum" Then
                Dim Mo As Double
                Mo = 95.941
                Dim Output As Double
                Output = InputConvert / Mo
                lblEquals.Text = Output
            End If

            If ElementType = "Nd Neodymium" Then
                Dim Nd As Double
                Nd = 144.24
                Dim Output As Double
                Output = InputConvert / Nd
                lblEquals.Text = Output
            End If

            If ElementType = "Ne Neon" Then
                Dim Ne As Double
                Ne = 20.1797
                Dim Output As Double
                Output = InputConvert / Ne
                lblEquals.Text = Output
            End If

            If ElementType = "Np Neptunium" Then
                Dim Np As Double
                Np = 237.048
                Dim Output As Double
                Output = InputConvert / Np
                lblEquals.Text = Output
            End If

            If ElementType = "Ni Nickel" Then
                Dim Ni As Double
                Ni = 58.6934
                Dim Output As Double
                Output = InputConvert / Ni
                lblEquals.Text = Output
            End If

            If ElementType = "Nb Niobium" Then
                Dim Nb As Double
                Nb = 92.90638
                Dim Output As Double
                Output = InputConvert / Nb
                lblEquals.Text = Output
            End If

            If ElementType = "N Nitrogen" Then
                Dim N As Double
                N = 14.00674
                Dim Output As Double
                Output = InputConvert / N
                lblEquals.Text = Output
            End If

            If ElementType = "No Nobelium" Then
                Dim No As Double
                No = 259
                Dim Output As Double
                Output = InputConvert / No
                lblEquals.Text = Output
            End If

            If ElementType = "Os Osmium" Then
                Dim Os As Double
                Os = 190.21
                Dim Output As Double
                Output = InputConvert / Os
                lblEquals.Text = Output
            End If

            If ElementType = "O Oxygen" Then
                Dim O As Double
                O = 15.9994
                Dim Output As Double
                Output = InputConvert / O
                lblEquals.Text = Output
            End If

            If ElementType = "Pd Palladium" Then
                Dim Pd As Double
                Pd = 106.421
                Dim Output As Double
                Output = InputConvert / Pd
                lblEquals.Text = Output
            End If

            If ElementType = "P Phosphorus" Then
                Dim P As Double
                P = 30.9737624
                Dim Output As Double
                Output = InputConvert / P
                lblEquals.Text = Output
            End If

            If ElementType = "Pt Platinum" Then
                Dim Pt As Double
                Pt = 195.083
                Dim Output As Double
                Output = InputConvert / Pt
                lblEquals.Text = Output
            End If

            If ElementType = "Pu Plutonium" Then
                Dim Pu As Double
                Pu = 244
                Dim Output As Double
                Output = InputConvert / Pu
                lblEquals.Text = Output
            End If

            If ElementType = "Po Polonium" Then
                Dim Po As Double
                Po = 209
                Dim Output As Double
                Output = InputConvert / Po
                lblEquals.Text = Output
            End If

            If ElementType = "K Potassium" Then
                Dim K As Double
                K = 39.0983
                Dim Output As Double
                Output = InputConvert / K
                lblEquals.Text = Output
            End If

            If ElementType = "Pr Praseodymium" Then
                Dim Pr As Double
                Pr = 140.907653
                Dim Output As Double
                Output = InputConvert / Pr
                lblEquals.Text = Output
            End If

            If ElementType = "Pm Promethium" Then
                Dim Pm As Double
                Pm = 145
                Dim Output As Double
                Output = InputConvert / Pm
                lblEquals.Text = Output
            End If

            If ElementType = "Pa Protactinium" Then
                Dim Pa As Double
                Pa = 231.0359
                Dim Output As Double
                Output = InputConvert / Pa
                lblEquals.Text = Output
            End If

            If ElementType = "Ra Radium" Then
                Dim Ra As Double
                Ra = 226.025
                Dim Output As Double
                Output = InputConvert / Ra
                lblEquals.Text = Output
            End If

            If ElementType = "Rn Radon" Then
                Dim Rn As Double
                Rn = 222
                Dim Output As Double
                Output = InputConvert / Rn
                lblEquals.Text = Output
            End If

            If ElementType = "Re Rhenium" Then
                Dim Re As Double
                Re = 186.2071
                Dim Output As Double
                Output = InputConvert / Re
                lblEquals.Text = Output
            End If

            If ElementType = "Rh Rhodium" Then
                Dim Rh As Double
                Rh = 102.9055
                Dim Output As Double
                Output = InputConvert / Rh
                lblEquals.Text = Output
            End If

            If ElementType = "Rb Rubidium" Then
                Dim Rb As Double
                Rb = 85.4678
                Dim Output As Double
                Output = InputConvert / Rb
                lblEquals.Text = Output
            End If

            If ElementType = "Ru Ruthenium" Then
                Dim Ru As Double
                Ru = 101.07
                Dim Output As Double
                Output = InputConvert / Ru
                lblEquals.Text = Output
            End If

            If ElementType = "Rf Rutherfordium" Then
                Dim Rf As Double
                Rf = 261
                Dim Output As Double
                Output = InputConvert / Rf
                lblEquals.Text = Output
            End If

            If ElementType = "Sm Samarium" Then
                Dim Sm As Double
                Sm = 150.36
                Dim Output As Double
                Output = InputConvert / Sm
                lblEquals.Text = Output
            End If

            If ElementType = "Sc Scandium" Then
                Dim Sc As Double
                Sc = 44.95591
                Dim Output As Double
                Output = InputConvert / Sc
                lblEquals.Text = Output
            End If

            If ElementType = "Sg Seaborgium" Then
                Dim Sg As Double
                Sg = 263
                Dim Output As Double
                Output = InputConvert / Sg
                lblEquals.Text = Output
            End If

            If ElementType = "Se Selenium" Then
                Dim Se As Double
                Se = 78.96
                Dim Output As Double
                Output = InputConvert / Se
                lblEquals.Text = Output
            End If

            If ElementType = "Si Silicon" Then
                Dim Si As Double
                Si = 28.0855
                Dim Output As Double
                Output = InputConvert / Si
                lblEquals.Text = Output
            End If

            If ElementType = "Ag Silver" Then
                Dim Ag As Double
                Ag = 107.8682
                Dim Output As Double
                Output = InputConvert / Ag
                lblEquals.Text = Output
            End If

            If ElementType = "Na Sodium" Then
                Dim Na As Double
                Na = 22.989768
                Dim Output As Double
                Output = InputConvert / Na
                lblEquals.Text = Output
            End If

            If ElementType = "Sr Strontium" Then
                Dim Sr As Double
                Sr = 87.62
                Dim Output As Double
                Output = InputConvert / Sr
                lblEquals.Text = Output
            End If

            If ElementType = "S Sulphur" Then
                Dim S As Double
                S = 32.066
                Dim Output As Double
                Output = InputConvert / S
                lblEquals.Text = Output
            End If

            If ElementType = "Ta Tantalum" Then
                Dim Ta As Double
                Ta = 180.9479
                Dim Output As Double
                Output = InputConvert / Ta
                lblEquals.Text = Output
            End If

            If ElementType = "Tc Technetium" Then
                Dim Tc As Double
                Tc = 98
                Dim Output As Double
                Output = InputConvert / Tc
                lblEquals.Text = Output
            End If

            If ElementType = "Te Tellurium" Then
                Dim Te As Double
                Te = 127.603
                Dim Output As Double
                Output = InputConvert / Te
                lblEquals.Text = Output
            End If

            If ElementType = "Tb Terbium" Then
                Dim Tb As Double
                Tb = 158.92534
                Dim Output As Double
                Output = InputConvert / Tb
                lblEquals.Text = Output
            End If

            If ElementType = "Tl Thallium" Then
                Dim Tl As Double
                Tl = 204.3833
                Dim Output As Double
                Output = InputConvert / Tl
                lblEquals.Text = Output
            End If

            If ElementType = "Th Thorium" Then
                Dim Th As Double
                Th = 232.0381
                Dim Output As Double
                Output = InputConvert / Th
                lblEquals.Text = Output
            End If

            If ElementType = "Tm Thulium" Then
                Dim Tm As Double
                Tm = 168.93421
                Dim Output As Double
                Output = InputConvert / Tm
                lblEquals.Text = Output
            End If

            If ElementType = "Sn Tin" Then
                Dim Sn As Double
                Sn = 118.71
                Dim Output As Double
                Output = InputConvert / Sn
                lblEquals.Text = Output
            End If

            If ElementType = "Ti Titanium" Then
                Dim Ti As Double
                Ti = 47.88
                Dim Output As Double
                Output = InputConvert / Ti
                lblEquals.Text = Output
            End If

            If ElementType = "W Tungsten" Then
                Dim W As Double
                W = 183.85
                Dim Output As Double
                Output = InputConvert / W
                lblEquals.Text = Output
            End If

            If ElementType = "U Uranium" Then
                Dim U As Double
                U = 238.0289
                Dim Output As Double
                Output = InputConvert / U
                lblEquals.Text = Output
            End If

            If ElementType = "V Vanadium" Then
                Dim V As Double
                V = 50.9415
                Dim Output As Double
                Output = InputConvert / V
                lblEquals.Text = Output
            End If

            If ElementType = "Xe Xenon" Then
                Dim Xe As Double
                Xe = 131.29
                Dim Output As Double
                Output = InputConvert / Xe
                lblEquals.Text = Output
            End If

            If ElementType = "Yb Ytterbium" Then
                Dim Yb As Double
                Yb = 173.04
                Dim Output As Double
                Output = InputConvert / Yb
                lblEquals.Text = Output
            End If

            If ElementType = "Y Yttrium" Then
                Dim Y As Double
                Y = 88.90585
                Dim Output As Double
                Output = InputConvert / Y
                lblEquals.Text = Output
            End If

            If ElementType = "Zn Zinc" Then
                Dim Zn As Double
                Zn = 65.39
                Dim Output As Double
                Output = InputConvert / Zn
                lblEquals.Text = Output
            End If

            If ElementType = "Zr Zirconium" Then
                Dim Zr As Double
                Zr = 91.224
                Dim Output As Double
                Output = InputConvert / Zr
                lblEquals.Text = Output
            End If

            'And now for something completely different!
            'These are the synthetic radioactive triple lettered elements. Some were also given actual
            'names which I've included as well

            'I used the masses of the most stable isotopes

            If ElementType = "Uub Ununbium" Then
                Dim Uub As Double
                Uub = 285
                Dim Output As Double
                Output = InputConvert / Uub
                lblEquals.Text = Output
            End If

            If ElementType = "Cn Copernicium" Then
                Dim Cn As Double
                Cn = 285
                Dim Output As Double
                Output = InputConvert / Cn
                lblEquals.Text = Output
            End If

            If ElementType = "Uuh Ununhexium" Then
                Dim Uuh As Double
                Uuh = 293
                Dim Output As Double
                Output = InputConvert / Uuh
                lblEquals.Text = Output
            End If

            If ElementType = "Uun Ununnilium" Then
                Dim Uun As Double
                Uun = 281
                Dim Output As Double
                Output = InputConvert / Uun
                lblEquals.Text = Output
            End If

            If ElementType = "Ds Darmstadtium" Then
                Dim Ds As Double
                Ds = 281
                Dim Output As Double
                Output = InputConvert / Ds
                lblEquals.Text = Output
            End If

            If ElementType = "Uuo Ununoctium" Then
                Dim Uuo As Double
                Uuo = 294
                Dim Output As Double
                Output = InputConvert / Uuo
                lblEquals.Text = Output
            End If

            If ElementType = "Uup Ununpentium" Then
                Dim Uup As Double
                Uup = 289
                Dim Output As Double
                Output = InputConvert / Uup
                lblEquals.Text = Output
            End If

            If ElementType = "Uuq Ununquadium" Then
                Dim Uuq As Double
                Uuq = 289
                Dim Output As Double
                Output = InputConvert / Uuq
                lblEquals.Text = Output
            End If

            If ElementType = "Uus Ununseptium" Then
                Dim Uus As Double
                Uus = 294
                Dim Output As Double
                Output = InputConvert / Uus
                lblEquals.Text = Output
            End If

            If ElementType = "Uut Ununtrium" Then
                Dim Uut As Double
                Uut = 286
                Dim Output As Double
                Output = InputConvert / Uut
                lblEquals.Text = Output
            End If

            If ElementType = "Uuu Ununumium" Then
                Dim Uuu As Double
                Uuu = 281
                Dim Output As Double
                Output = InputConvert / Uuu
                lblEquals.Text = Output
            End If

            If ElementType = "Rg Roentgenium" Then
                Dim Rg As Double
                Rg = 281
                Dim Output As Double
                Output = InputConvert / Rg
                lblEquals.Text = Output
            End If

            Label12.Text = "moles"
        End If
    End Sub
End Class

```
As of now I'm going through Wikipedia and getting all the info.

---

### Post by Legendary_Bibo on 2010-08-17
Screenshot of it. Um...mind the take screenshot menu. I haven't fully labeled the element panel, the calculate form is complete except for writing work arounds.

---

### Post by linux18 on 2010-08-17
wow! thats programming right there!

---

### Post by schauerlich on 2010-08-17
Oh... oh my...

You do know this is what databases are for, right? And arrays? And for loops? And objects?


> **linux18 said:**
> wow! thats programming right there!

Don't encourage him...

---

### Post by Austin25 on 2010-08-17
Nice, but Visual Basic supposedly teaches bad habits.

---

### Post by Legendary_Bibo on 2010-08-17
> **schauerlich said:**
> Oh... oh my...

You do know this is what databases are for, right? And arrays? And for loops? And objects?

I'm using arrays on the information stuff on the periodic table. I don't see how loops would help me. Wait, which part are you referring to?

Wait I just realized you're right. I could have cut out a lot of typing if I turned that combo box into an array. Damnit! :mad:

---

### Post by schauerlich on 2010-08-17
> **Legendary_Bibo said:**
> I'm using arrays on the information stuff on the periodic table. I don't see how loops would help me. Wait, which part are you referring to?

Wait I just realized you're right. I could have cut out a lot of typing if I turned that combo box into an array. Damnit! :mad:

Here's a tip from the pros:

If you have to copy and paste 120 times and make small changes to each one, STOP. There is a much better, more general way to do it that will save you time and effort.

I'd start by making an element object, and a database which contains all of the information on the elements. There's no real way to get around providing all of the data, but there are MUCH better ways of doing it than hard coding it in for every element...

EDIT: hey, you don't even have to provide the info yourself. Chances are, if you're trying to do something, [someone else has already done it better than you can.](http://akiscode.com/pt/) This principle rarely changes unless you're doing something far-out and unique.

---

### Post by whiskeylover on 2010-08-17
> **Legendary_Bibo said:**
> 
Periodic Table Main Form:
```

snip

```As of now I'm going through Wikipedia and getting all the info.

This is an example of how not to write code.

Instead of creating each button individually, you could have created an array, each button getting its text from a database. And creating an evenhandler on the fly for each button.

Same goes for your calculate form. Instead of comparing the Text, you could've compared the IDs or something.

The whole bunch of 

```
If ElementType = "Al Aluminum" Then
                Dim Al As Double
                Al = 23.982
                Dim Output As Double
                Output = InputConvert * Al
                lblEquals.Text = Output
            End If
```statements could have been replaced by a single IF statement like this...
 ```
Dim element As Double
                element = ElementWeights[ElementId]
                Dim Output As Double
                Output = InputConvert * element
                lblEquals.Text = Output
```

---

### Post by Legendary_Bibo on 2010-08-17
> **Austin25 said:**
> Nice, but Visual Basic supposedly teaches bad habits.

Yeah I know, but school starts in a week, and I know VB from my class. I would have to spend a while getting used to another gui development environment, and whatnot.

---

### Post by juancarlospaco on 2010-08-17
*I hope a LiGNUx version soon* :)

---

### Post by Legendary_Bibo on 2010-08-17
> **whiskeylover said:**
> This is an example of how not to write code.

Instead of creating each button individually, you could have created an array, each button getting its text from a database. And creating an evenhandler on the fly for each button.

Same goes for your calculate form. Instead of comparing the Text, you could've compared the IDs or something.

The whole bunch of 

```
If ElementType = "Al Aluminum" Then
                Dim Al As Double
                Al = 23.982
                Dim Output As Double
                Output = InputConvert * Al
                lblEquals.Text = Output
            End If
```statements could have been replaced by a single IF statement like this...
 ```
Dim element As Double
                element = ElementWeights[ElementId]
                Dim Output As Double
                Output = InputConvert * element
                lblEquals.Text = Output
```

Like an online Database? Or you mean make my own?

I think I'm going to use individual arrays for each element rather than link to a database. I believe it would take as much time coding it, and it would be easier for me to read it in the future.

These are great tips guys, thanks!

---

### Post by nvteighen on 2010-08-17
Professional programmers try to unify stuff into common structures so they don't have to repeat the same code over and over. There are several different approaches, some better for some situations than other, but that's the idea. So, what I've had done is to create something that somehow holds all information on an element and give that something, usually a "class" or a complex data structure (a complex user-defined type), some capabilities... for example, if I got the element H, be able to do H.getAtomicNumber() and get 1 or He.getAtomicNumber() and get 2. Then the GUI would be an afterthought that just calls those underlying things and present them nice and cleanly to the user.

The issue with VB is that leads beginners to first construct the GUI and code under each desired event code section... repeating lines of code in different places. Why? Because creating functions and stuff is, IIRC, restricted to Modules and Class Modules and that's more difficult to manage. VB makes it easier for the beginner to do the wrong thing, while, C, C++, Java, etc. operate the other way around.

Look at the Programming Talk forum for further information.

---

### Post by whiskeylover on 2010-08-17
> **Legendary_Bibo said:**
> Like an online Database? Or you mean make my own?

I think I'm going to use individual arrays for each element rather than link to a database. I believe it would take as much time coding it, and it would be easier for me to read it in the future.

These are great tips guys, thanks!

The easiest way to do it would be to use arrays. If the contents of that array change frequently, then use a SQL Server DB. It integrates well with VB.

---

### Post by Legendary_Bibo on 2010-08-17
> **whiskeylover said:**
> The easiest way to do it would be to use arrays. If the contents of that array change frequently, then use a SQL Server DB. It integrates well with VB.

Ah gotcha! Arrays it is then. I actually have the bad habit of making the decision on how to go about tasks when I'm tired, which ends up with me doing things an extremely long way, and using more variables than I need. If I had done it wide awake I would have realized that. When I make the linux version I'm definitely taking your advice to heart.

---

### Post by GenBattle on 2010-08-17
I started in VB as well, but i wouldn't rely on VB as anything more than a starting point. You seem to have done very well going the way you are, but as other have said, you can probably at least halve the amount of code you've written by using OOP or some other paradigm to structure what you are doing.

My approach would be to make and element class with properties like atomic mass and related methods, then subclass for objects like PreciousMetal, PoorMetal, etc. if you need specific properties/methods for those classes. You could definitely replace 99% of those onClick handlers with a single handler which takes the sender object with all of the appropriate properties attached, then use the the properties of the sender to determine the action you take in the handler. I haven't used VB for almost a decade though, so i can't give any specific advice for that language.

Writing programs is alot of trouble though, and i all too commonly find myself getting frustrated with clients who don't understand the underlying complexity that goes into computer programs. Making any change after you've already built the app is always going to cause untold headaches. This is why requirements gathering and design at the start of a project are so important. That said, you're never going to pin a client down to exactly what they want until they see it working in front of them :p

---

### Post by Legendary_Bibo on 2010-08-17
> **GenBattle said:**
> I started in VB as well, but i wouldn't rely on VB as anything more than a starting point. You seem to have done very well going the way you are, but as other have said, you can probably at least halve the amount of code you've written by using OOP or some other paradigm to structure what you are doing.

My approach would be to make and element class with properties like atomic mass and related methods, then subclass for objects like PreciousMetal, PoorMetal, etc. if you need specific properties/methods for those classes. You could definitely replace 99% of those onClick handlers with a single handler which takes the sender object with all of the appropriate properties attached, then use the the properties of the sender to determine the action you take in the handler. I haven't used VB for almost a decade though, so i can't give any specific advice for that language.

Writing programs is alot of trouble though, and i all too commonly find myself getting frustrated with clients who don't understand the underlying complexity that goes into computer programs. Making any change after you've already built the app is always going to cause untold headaches. This is why requirements gathering and design at the start of a project are so important. That said, you're never going to pin a client down to exactly what they want until they see it working in front of them :p

Well I just got back into using VB so I figured I would use what I know and if I come across easier methods then that's what I'll do. I have to learn to plan things out before 2am or else my mind can only think of If statements. You should see my C++ programs I made for a class. I don't know what I was thinking. I know for now it's not the fastest way of doing things, but it makes it easier for me to learn and understand. Also I have a habit of making things easier for someone else to read and understand. In my C++ class I wrote more documentation than code on every program explaining everything as clearly and in plain english as possible so that even a non-programmer understood everything. I literally broke down every step. I had a hard time with C++ so I was confused when my professor said I should be a programmer some day. Now I realize why.

---

### Post by GenBattle on 2010-08-17
C++ is not an easy language to learn, and C++ is certainly not the easiest way to attack most problems.

The reason VB is terrible is largely because it does not promote proper program structure, and does not require knowledge of fundamental programming concepts to use. The upshot is that this makes it extremely easy to use.

Modern scripting languages like Python, Ruby, etc. will give you most of the ease of use with much more structure. Languages like Java/C# are more structured, but still allow you to ignore details like memory allocation/deallocation. C++ adds in memory allocation plus a huge range of other tools which, if you don't know how to use them properly yet, simply serve to confuse you further.

Programming skills can be taught, but it's really hard to teach people to write good documentation ;)

---

### Post by jim_24601 on 2010-08-18
> **linux18 said:**
> might want to edit your post, so you won't get a warning/infraction (remove instances of the 'B' word)

Basic?

---

