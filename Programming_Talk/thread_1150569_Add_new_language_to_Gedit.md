---
title: "Add new language to Gedit"
date: 2009-05-06
forum: Programming Talk
---

### Post by Eider on 2009-05-06
I have a language file for jEdit and I want to convert that to a language file that can be used in Gedit.

I don't know if there is a tool available that automatically converts the language file. Otherwise I can convert it by hand, but I can't find much help to write a language file for Gedit.


Thanks,
Eider

---

### Post by salvachn on 2009-05-06
I wonder why you would do that? jedit is richer than gedit in terms of features and plugins. And I think gedit uses an XML DTD to specify language files. You'll need to copy it to this directory: usr/share/gtksourceview-1.0/language-specs

---

### Post by salvachn on 2009-05-06
The directory may well be:  
/usr/share/gtksourceview-2.0/language-specs

---

### Post by Eider on 2009-05-10
I don't get my Lilypond.lang file to work properly.

My .lang file:
```

<?xml version="1.0" encoding="UTF-8"?>
<language id="ly" _name="Lilypond" version="1.0" _section="Others">
  <metadata>
    <property name="mimetypes">text/x-lilypond</property>
    <property name="globs">*.ly</property>
    <property name="block-comment-start">%{</property>
    <property name="block-comment-end">%}</property>
    <property name="line-comment-start">%</property>
  </metadata>

  <styles>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="quotation" _name="Quotation" map-to="lilypond:quotation"/>
    <style id="line-comment" _name="Line Comment" map-to="def:line-comment"/>
    <style id="octave" _name="Octave" map-to="lilypond:octave"/>
    <style id="brackets" _name="Brackets" map-to="lilypond:brackets"/>
    <style id="mensural-notation" _name="Mensural Notation" map-to="lilypond:mensural-notation"/>
    <style id="internal-commands" _name="Internal Commands" map-to="lilypond:internal-commands"/>
    <style id="music-functions" _name="Music Functions" map-to="lilypond:music-functions"/>
    <style id="markup-commands" _name="Markup Commands" map-to="lilypond:markup-commands"/>
    <style id="identifiers" _name="Identifiers" map-to="lilypond:identifiers"/>
    <style id="lykeyword" _name="Keywords" map-to="lilypond:lykeyword"/>
  </styles>

  <definitions>

    <context id="comment" style-ref="comment">
      <start>%{</start>
      <end>%}</end>
      <include>
        <context style-ref="error" extend-parent="false">
          <match>%{</match>
        </context>
        <context ref="def:in-comment"/>
      </include>
    </context>

    <context id="quotation" style-ref="quotation">
      <start>"</start>
      <end>"</end>
      <include>
        <context style-ref="error" extend-parent="false">
          <match>"</match>
        </context>
        <context ref="def:quotation"/>
      </include>
    </context>

    <context id="line-comment" style-ref="comment" end-at-line-end="true" extend-parent="false">
      <start>%</start>
      <include>
        <context ref="def:line-comment"/>
      </include>
    </context>

   <context id="octave" style-ref="octave">
	<keyword>,</keyword>
	<keyword>'</keyword>
   </context>

   <context id="brackets" style-ref="internal-commands">
	<keyword>{</keyword>
	<keyword>}</keyword>
	<keyword>[</keyword>
	<keyword>]</keyword>
	<keyword>&lt;&lt;</keyword>
	<keyword>&gt;&gt;</keyword>
   </context>

   <context id="mensural-notation" style-ref="mensural-notation">
	<keyword>reve</keyword>
	<keyword>\longa</keyword>
	<keyword>\maxima</keyword>
   </context>

   <context id="internal-commands" style-ref="internal-commands">
	<keyword>\override</keyword>
	<keyword>\version</keyword>
	<keyword>\include</keyword>
	<keyword>\invalid</keyword>
	<keyword>\addquote</keyword>
	<keyword>\alternative</keyword>
	<keyword>\book</keyword>
	<keyword>\~</keyword>
	<keyword>\mark</keyword>
	<keyword>\default</keyword>
	<keyword>\key</keyword>
	<keyword>\skip</keyword>
	<keyword>\octave</keyword>
	<keyword>\partial</keyword>
	<keyword>\time</keyword>
	<keyword>\change</keyword>
	<keyword>\consists</keyword>
	<keyword>\remove</keyword>
	<keyword>\accepts</keyword>
	<keyword>\defaultchild</keyword>
	<keyword>\denies</keyword>
	<keyword>\alias</keyword>
	<keyword>\type</keyword>
	<keyword>\description</keyword>
	<keyword>\name</keyword>
	<keyword>\context</keyword>
	<keyword>\grobdescriptions</keyword>
	<keyword>\markup</keyword>
	<keyword>\header</keyword>
	<keyword>\notemode</keyword>
	<keyword>\drummode</keyword>
	<keyword>\figuremode</keyword>
	<keyword>\chordmode</keyword>
	<keyword>\lyricmode</keyword>
	<keyword>\drums</keyword>
	<keyword>\figures</keyword>
	<keyword>\chords</keyword>
	<keyword>\lyrics</keyword>
	<keyword>\once</keyword>
	<keyword>\revert</keyword>
	<keyword>\set</keyword>
	<keyword>\unset</keyword>
	<keyword>\addlyrics</keyword>
	<keyword>\objectid</keyword>
	<keyword>\with</keyword>
	<keyword>\rest</keyword>
	<keyword>\paper</keyword>
	<keyword>\midi</keyword>
	<keyword>\layout</keyword>
	<keyword>\new</keyword>
	<keyword>\times</keyword>
	<keyword>\transpose</keyword>
	<keyword>\tag</keyword>
	<keyword>\relative</keyword>
	<keyword>\renameinput</keyword>
	<keyword>\repeat</keyword>
	<keyword>\lyricsto</keyword>
	<keyword>\score</keyword>
	<keyword>\sequential</keyword>
	<keyword>\simultaneous</keyword>
	<keyword>\longa</keyword>
	<keyword>\breve</keyword>
	<keyword>\maxima</keyword>
	<keyword>\tempo</keyword>
   </context>

   <context id="identifiers" style-ref="identifiers">
	<keyword>\override</keyword>
	<keyword>\version</keyword>
	<keyword>\include</keyword>
	<keyword>\invalid</keyword>
	<keyword>\addquote</keyword>
	<keyword>\alternative</keyword>
	<keyword>\book</keyword>
	<keyword>\~</keyword>
	<keyword>\mark</keyword>
	<keyword>\default</keyword>
	<keyword>\key</keyword>
	<keyword>\skip</keyword>
	<keyword>\octave</keyword>
	<keyword>\partial</keyword>
	<keyword>\time</keyword>
	<keyword>\change</keyword>
	<keyword>\consists</keyword>
	<keyword>\remove</keyword>
	<keyword>\accepts</keyword>
	<keyword>\defaultchild</keyword>
	<keyword>\denies</keyword>
	<keyword>\alias</keyword>
	<keyword>\type</keyword>
	<keyword>\description</keyword>
	<keyword>\name</keyword>
	<keyword>\context</keyword>
	<keyword>\grobdescriptions</keyword>
	<keyword>\markup</keyword>
	<keyword>\header</keyword>
	<keyword>\notemode</keyword>
	<keyword>\drummode</keyword>
	<keyword>\figuremode</keyword>
	<keyword>\chordmode</keyword>
	<keyword>\lyricmode</keyword>
	<keyword>\drums</keyword>
	<keyword>\figures</keyword>
	<keyword>\chords</keyword>
	<keyword>\lyrics</keyword>
	<keyword>\once</keyword>
	<keyword>\revert</keyword>
	<keyword>\set</keyword>
	<keyword>\unset</keyword>
	<keyword>\addlyrics</keyword>
	<keyword>\objectid</keyword>
	<keyword>\with</keyword>
	<keyword>\rest</keyword>
	<keyword>\paper</keyword>
	<keyword>\midi</keyword>
	<keyword>\layout</keyword>
	<keyword>\new</keyword>
	<keyword>\times</keyword>
	<keyword>\transpose</keyword>
	<keyword>\tag</keyword>
	<keyword>\relative</keyword>
	<keyword>\renameinput</keyword>
	<keyword>\repeat</keyword>
	<keyword>\lyricsto</keyword>
	<keyword>\score</keyword>
	<keyword>\sequential</keyword>
	<keyword>\simultaneous</keyword>
	<keyword>\longa</keyword>
	<keyword>\breve</keyword>
	<keyword>\maxima</keyword>
	<keyword>\tempo</keyword>
	<keyword>\AncientRemoveEmptyStaffContext</keyword>
	<keyword>\RemoveEmptyRhythmicStaffContext</keyword>
	<keyword>\RemoveEmptyStaffContext</keyword>
	<keyword>\accent</keyword>
	<keyword>\aeolian</keyword>
	<keyword>\afterGraceFraction</keyword>
	<keyword>\aikenHeads</keyword>
	<keyword>\arpeggio</keyword>
	<keyword>\arpeggioArrowDown</keyword>
	<keyword>\arpeggioArrowUp</keyword>
	<keyword>\arpeggioBracket</keyword>
	<keyword>\arpeggioNormal</keyword>
	<keyword>\arpeggioParenthesis</keyword>
	<keyword>\autoBeamOff</keyword>
	<keyword>\autoBeamOn</keyword>
	<keyword>\balloonLengthOff</keyword>
	<keyword>\balloonLengthOn</keyword>
	<keyword>\bassFigureExtendersOff</keyword>
	<keyword>\bassFigureExtendersOn</keyword>
	<keyword>\bassFigureStaffAlignmentDown</keyword>
	<keyword>\bassFigureStaffAlignmentNeutral</keyword>
	<keyword>\bassFigureStaffAlignmentUp</keyword>
	<keyword>\between-system-padding</keyword>
	<keyword>\between-system-space</keyword>
	<keyword>\bigger</keyword>
	<keyword>\blackTriangleMarkup</keyword>
	<keyword>\bookTitleMarkup</keyword>
	<keyword>\bracketCloseSymbol</keyword>
	<keyword>\bracketOpenSymbol</keyword>
	<keyword>\break</keyword>
	<keyword>\breve</keyword>
	<keyword>\cadenzaOff</keyword>
	<keyword>\cadenzaOn</keyword>
	<keyword>\center</keyword>
	<keyword>\chordmodifiers</keyword>
	<keyword>\cm</keyword>
	<keyword>\coda</keyword>
	<keyword>\compressFullBarRests</keyword>
	<keyword>\cr</keyword>
	<keyword>\cresc</keyword>
	<keyword>\crescHairpin</keyword>
	<keyword>\crescTextCresc</keyword>
	<keyword>\decr</keyword>
	<keyword>\defaultTimeSignature</keyword>
	<keyword>\dim</keyword>
	<keyword>\dimHairpin</keyword>
	<keyword>\dimTextDecr</keyword>
	<keyword>\dimTextDecresc</keyword>
	<keyword>\dimTextDim</keyword>
	<keyword>\dorian</keyword>
	<keyword>\dotsDown</keyword>
	<keyword>\dotsNeutral</keyword>
	<keyword>\dotsUp</keyword>
	<keyword>\down</keyword>
	<keyword>\downbow</keyword>
	<keyword>\downmordent</keyword>
	<keyword>\downprall</keyword>
	<keyword>\drumPitchNames</keyword>
	<keyword>\dutchPitchnames</keyword>
	<keyword>\dynamicDown</keyword>
	<keyword>\dynamicNeutral</keyword>
	<keyword>\dynamicUp</keyword>
	<keyword>\easyHeadsOff</keyword>
	<keyword>\easyHeadsOn</keyword>
	<keyword>\endcr</keyword>
	<keyword>\endcresc</keyword>
	<keyword>\enddecr</keyword>
	<keyword>\enddim</keyword>
	<keyword>\endincipit</keyword>
	<keyword>\escapedBiggerSymbol</keyword>
	<keyword>\escapedExclamationSymbol</keyword>
	<keyword>\escapedParenthesisCloseSymbol</keyword>
	<keyword>\escapedParenthesisOpenSymbol</keyword>
	<keyword>\escapedSmallerSymbol</keyword>
	<keyword>\espressivo</keyword>
	<keyword>\evenHeaderMarkup</keyword>
	<keyword>\expandFullBarRests</keyword>
	<keyword>\f</keyword>
	<keyword>\fermata</keyword>
	<keyword>\fermataMarkup</keyword>
	<keyword>\ff</keyword>
	<keyword>\fff</keyword>
	<keyword>\ffff</keyword>
	<keyword>\first-page-number</keyword>
	<keyword>\flageolet</keyword>
	<keyword>\fp</keyword>
	<keyword>\frenchChords</keyword>
	<keyword>\fullJazzExceptions</keyword>
	<keyword>\fz</keyword>
	<keyword>\germanChords</keyword>
	<keyword>\glissando</keyword>
	<keyword>\harmonic</keyword>
	<keyword>\hideNotes</keyword>
	<keyword>\hideStaffSwitch</keyword>
	<keyword>\huge</keyword>
	<keyword>\ignatzekExceptionMusic</keyword>
	<keyword>\ignatzekExceptions</keyword>
	<keyword>\improvisationOff</keyword>
	<keyword>\improvisationOn</keyword>
	<keyword>\in</keyword>
	<keyword>\instrument-definitions</keyword>
	<keyword>\ionian</keyword>
	<keyword>\italianChords</keyword>
	<keyword>\laissezVibrer</keyword>
	<keyword>\large</keyword>
	<keyword>\left</keyword>
	<keyword>\lheel</keyword>
	<keyword>\lineprall</keyword>
	<keyword>\locrian</keyword>
	<keyword>\longa</keyword>
	<keyword>\longfermata</keyword>
	<keyword>\ltoe</keyword>
	<keyword>\lydian</keyword>
	<keyword>\major</keyword>
	<keyword>\marcato</keyword>
	<keyword>\maxima</keyword>
	<keyword>\melisma</keyword>
	<keyword>\melismaEnd</keyword>
	<keyword>\mergeDifferentlyDottedOff</keyword>
	<keyword>\mergeDifferentlyDottedOn</keyword>
	<keyword>\mergeDifferentlyHeadedOff</keyword>
	<keyword>\mergeDifferentlyHeadedOn</keyword>
	<keyword>\mf</keyword>
	<keyword>\midiDrumPitches</keyword>
	<keyword>\minor</keyword>
	<keyword>\mixolydian</keyword>
	<keyword>\mm</keyword>
	<keyword>\mordent</keyword>
	<keyword>\mp</keyword>
	<keyword>\newSpacingSection</keyword>
	<keyword>\noBeam</keyword>
	<keyword>\noBreak</keyword>
	<keyword>\normalsize</keyword>
	<keyword>\numericTimeSignature</keyword>
	<keyword>\oddFooterMarkup</keyword>
	<keyword>\oddHeaderMarkup</keyword>
	<keyword>\oneVoice</keyword>
	<keyword>\open</keyword>
	<keyword>\output-scale</keyword>
	<keyword>\p</keyword>
	<keyword>\page-limit-inter-system-space</keyword>
	<keyword>\page-top-space</keyword>
	<keyword>\parenthesisCloseSymbol</keyword>
	<keyword>\parenthesisOpenSymbol</keyword>
	<keyword>\partialJazzExceptions</keyword>
	<keyword>\partialJazzMusic</keyword>
	<keyword>\phrasingSlurDashed</keyword>
	<keyword>\phrasingSlurDotted</keyword>
	<keyword>\phrasingSlurDown</keyword>
	<keyword>\phrasingSlurNeutral</keyword>
	<keyword>\phrasingSlurSolid</keyword>
	<keyword>\phrasingSlurUp</keyword>
	<keyword>\phrygian</keyword>
	<keyword>\pipeSymbol</keyword>
	<keyword>\pitchnames</keyword>
	<keyword>\portato</keyword>
	<keyword>\pp</keyword>
	<keyword>\ppp</keyword>
	<keyword>\pppp</keyword>
	<keyword>\ppppp</keyword>
	<keyword>\prall</keyword>
	<keyword>\pralldown</keyword>
	<keyword>\prallmordent</keyword>
	<keyword>\prallprall</keyword>
	<keyword>\prallup</keyword>
	<keyword>\predefinedFretboardsOff</keyword>
	<keyword>\predefinedFretboardsOn</keyword>
	<keyword>\print-first-page-number</keyword>
	<keyword>\print-page-number</keyword>
	<keyword>\pt</keyword>
	<keyword>\ragged-bottom</keyword>
	<keyword>\ragged-last-bottom</keyword>
	<keyword>\repeatTie</keyword>
	<keyword>\reverseturn</keyword>
	<keyword>\rfz</keyword>
	<keyword>\rheel</keyword>
	<keyword>\right</keyword>
	<keyword>\rtoe</keyword>
	<keyword>\sacredHarpHeads</keyword>
	<keyword>\scoreTitleMarkup</keyword>
	<keyword>\segno</keyword>
	<keyword>\semiGermanChords</keyword>
	<keyword>\setDefaultDurationToQuarter</keyword>
	<keyword>\sf</keyword>
	<keyword>\sff</keyword>
	<keyword>\sfp</keyword>
	<keyword>\sfz</keyword>
	<keyword>\shiftOff</keyword>
	<keyword>\shiftOn</keyword>
	<keyword>\shiftOnn</keyword>
	<keyword>\shiftOnnn</keyword>
	<keyword>\shortfermata</keyword>
	<keyword>\showStaffSwitch</keyword>
	<keyword>\signumcongruentiae</keyword>
	<keyword>\slashSeparator</keyword>
	<keyword>\slurDashed</keyword>
	<keyword>\slurDotted</keyword>
	<keyword>\slurDown</keyword>
	<keyword>\slurNeutral</keyword>
	<keyword>\slurSolid</keyword>
	<keyword>\slurUp</keyword>
	<keyword>\small</keyword>
	<keyword>\smaller</keyword>
	<keyword>\sostenutoOff</keyword>
	<keyword>\sostenutoOn</keyword>
	<keyword>\sp</keyword>
	<keyword>\spp</keyword>
	<keyword>\staccatissimo</keyword>
	<keyword>\staccato</keyword>
	<keyword>\start</keyword>
	<keyword>\startAcciaccaturaMusic</keyword>
	<keyword>\startAppoggiaturaMusic</keyword>
	<keyword>\startGraceMusic</keyword>
	<keyword>\startGroup</keyword>
	<keyword>\startStaff</keyword>
	<keyword>\startTextSpan</keyword>
	<keyword>\startTrillSpan</keyword>
	<keyword>\stemDown</keyword>
	<keyword>\stemNeutral</keyword>
	<keyword>\stemUp</keyword>
	<keyword>\stop</keyword>
	<keyword>\stopAcciaccaturaMusic</keyword>
	<keyword>\stopAppoggiaturaMusic</keyword>
	<keyword>\stopGraceMusic</keyword>
	<keyword>\stopGroup</keyword>
	<keyword>\stopStaff</keyword>
	<keyword>\stopTextSpan</keyword>
	<keyword>\stopTrillSpan</keyword>
	<keyword>\stopped</keyword>
	<keyword>\sustainOff</keyword>
	<keyword>\sustainOn</keyword>
	<keyword>\tagline</keyword>
	<keyword>\teeny</keyword>
	<keyword>\tenuto</keyword>
	<keyword>\textLengthOff</keyword>
	<keyword>\textLengthOn</keyword>
	<keyword>\textSpannerDown</keyword>
	<keyword>\textSpannerNeutral</keyword>
	<keyword>\textSpannerUp</keyword>
	<keyword>\thumb</keyword>
	<keyword>\tieDashed</keyword>
	<keyword>\tieDotted</keyword>
	<keyword>\tieDown</keyword>
	<keyword>\tieNeutral</keyword>
	<keyword>\tieSolid</keyword>
	<keyword>\tieUp</keyword>
	<keyword>\tildeSymbol</keyword>
	<keyword>\tiny</keyword>
	<keyword>\tocItemMarkup</keyword>
	<keyword>\tocTitleMarkup</keyword>
	<keyword>\treCorde</keyword>
	<keyword>\trill</keyword>
	<keyword>\tupletDown</keyword>
	<keyword>\tupletNeutral</keyword>
	<keyword>\tupletUp</keyword>
	<keyword>\turn</keyword>
	<keyword>\unHideNotes</keyword>
	<keyword>\unaCorda</keyword>
	<keyword>\unit</keyword>
	<keyword>\up</keyword>
	<keyword>\upbow</keyword>
	<keyword>\upmordent</keyword>
	<keyword>\upprall</keyword>
	<keyword>\varcoda</keyword>
	<keyword>\verylongfermata</keyword>
	<keyword>\voiceFour</keyword>
	<keyword>\voiceFourStyle</keyword>
	<keyword>\voiceNeutralStyle</keyword>
	<keyword>\voiceOne</keyword>
	<keyword>\voiceOneStyle</keyword>
	<keyword>\voiceThree</keyword>
	<keyword>\voiceThreeStyle</keyword>
	<keyword>\voiceTwo</keyword>
	<keyword>\voiceTwoStyle</keyword>
	<keyword>\whiteTriangleMarkup</keyword>
   </context>

   <context id="music-functions" style-ref="music-functions">
	<keyword>\acciaccatura</keyword>
	<keyword>\addChordShape</keyword>
	<keyword>\addInstrumentDefinition</keyword>
	<keyword>\addQuote</keyword>
	<keyword>\afterGrace</keyword>
	<keyword>\allowPageTurn</keyword>
	<keyword>\applyContext</keyword>
	<keyword>\applyMusic</keyword>
	<keyword>\applyOutput</keyword>
	<keyword>\appoggiatura</keyword>
	<keyword>\assertBeamQuant</keyword>
	<keyword>\assertBeamSlope</keyword>
	<keyword>\autochange</keyword>
	<keyword>\balloonGrobText</keyword>
	<keyword>\balloonText</keyword>
	<keyword>\bar</keyword>
	<keyword>\barNumberCheck</keyword>
	<keyword>\bendAfter</keyword>
	<keyword>\breathe</keyword>
	<keyword>\clef</keyword>
	<keyword>\cueDuring</keyword>
	<keyword>\displayLilyMusic</keyword>
	<keyword>\displayMusic</keyword>
	<keyword>\endSpanners</keyword>
	<keyword>\featherDurations</keyword>
	<keyword>\grace</keyword>
	<keyword>\includePageLayoutFile</keyword>
	<keyword>\instrumentSwitch</keyword>
	<keyword>\keepWithTag</keyword>
	<keyword>\killCues</keyword>
	<keyword>\label</keyword>
	<keyword>\makeClusters</keyword>
	<keyword>\musicMap</keyword>
	<keyword>\noPageBreak</keyword>
	<keyword>\noPageTurn</keyword>
	<keyword>\octaveCheck</keyword>
	<keyword>\oldaddlyrics</keyword>
	<keyword>\ottava</keyword>
	<keyword>\overrideProperty</keyword>
	<keyword>\pageBreak</keyword>
	<keyword>\pageTurn</keyword>
	<keyword>\parallelMusic</keyword>
	<keyword>\parenthesize</keyword>
	<keyword>\partcombine</keyword>
	<keyword>\pitchedTrill</keyword>
	<keyword>\pointAndClickOff</keyword>
	<keyword>\pointAndClickOn</keyword>
	<keyword>\quoteDuring</keyword>
	<keyword>\removeWithTag</keyword>
	<keyword>\resetRelativeOctave</keyword>
	<keyword>\rightHandFinger</keyword>
	<keyword>\scaleDurations</keyword>
	<keyword>\scoreTweak</keyword>
	<keyword>\shiftDurations</keyword>
	<keyword>\spacingTweaks</keyword>
	<keyword>\storePredefinedDiagram</keyword>
	<keyword>\tag</keyword>
	<keyword>\tocItem</keyword>
	<keyword>\transposedCueDuring</keyword>
	<keyword>\transposition</keyword>
	<keyword>\tweak</keyword>
	<keyword>\unfoldRepeats</keyword>
	<keyword>\withMusicProperty</keyword>
   </context>

   <context id="markup-commands" style-ref="markup-commands">
	<keyword>\abs-fontsize</keyword>
	<keyword>\arrow-head</keyword>
	<keyword>\backslashed-digit</keyword>
	<keyword>\beam</keyword>
	<keyword>\bold</keyword>
	<keyword>\box</keyword>
	<keyword>\bracket</keyword>
	<keyword>\caps</keyword>
	<keyword>\center-align</keyword>
	<keyword>\center-column</keyword>
	<keyword>\char</keyword>
	<keyword>\circle</keyword>
	<keyword>\column</keyword>
	<keyword>\combine</keyword>
	<keyword>\concat</keyword>
	<keyword>\dir-column</keyword>
	<keyword>\doubleflat</keyword>
	<keyword>\doublesharp</keyword>
	<keyword>\draw-circle</keyword>
	<keyword>\draw-line</keyword>
	<keyword>\dynamic</keyword>
	<keyword>\epsfile</keyword>
	<keyword>\fill-line</keyword>
	<keyword>\filled-box</keyword>
	<keyword>\finger</keyword>
	<keyword>\flat</keyword>
	<keyword>\fontCaps</keyword>
	<keyword>\fontsize</keyword>
	<keyword>\fraction</keyword>
	<keyword>\fret-diagram</keyword>
	<keyword>\fret-diagram-terse</keyword>
	<keyword>\fret-diagram-verbose</keyword>
	<keyword>\fromproperty</keyword>
	<keyword>\general-align</keyword>
	<keyword>\halign</keyword>
	<keyword>\harp-pedal</keyword>
	<keyword>\hbracket</keyword>
	<keyword>\hcenter-in</keyword>
	<keyword>\hspace</keyword>
	<keyword>\huge</keyword>
	<keyword>\italic</keyword>
	<keyword>\justify</keyword>
	<keyword>\justify-field</keyword>
	<keyword>\justify-string</keyword>
	<keyword>\large</keyword>
	<keyword>\larger</keyword>
	<keyword>\left-align</keyword>
	<keyword>\left-column</keyword>
	<keyword>\line</keyword>
	<keyword>\lookup</keyword>
	<keyword>\lower</keyword>
	<keyword>\magnify</keyword>
	<keyword>\markalphabet</keyword>
	<keyword>\markletter</keyword>
	<keyword>\medium</keyword>
	<keyword>\musicglyph</keyword>
	<keyword>\natural</keyword>
	<keyword>\normal-size-sub</keyword>
	<keyword>\normal-size-super</keyword>
	<keyword>\normal-text</keyword>
	<keyword>\normalsize</keyword>
	<keyword>\note</keyword>
	<keyword>\note-by-number</keyword>
	<keyword>\null</keyword>
	<keyword>\number</keyword>
	<keyword>\on-the-fly</keyword>
	<keyword>\override</keyword>
	<keyword>\pad-around</keyword>
	<keyword>\pad-markup</keyword>
	<keyword>\pad-to-box</keyword>
	<keyword>\pad-x</keyword>
	<keyword>\page-ref</keyword>
	<keyword>\postscript</keyword>
	<keyword>\put-adjacent</keyword>
	<keyword>\raise</keyword>
	<keyword>\right-align</keyword>
	<keyword>\right-column</keyword>
	<keyword>\roman</keyword>
	<keyword>\rotate</keyword>
	<keyword>\rounded-box</keyword>
	<keyword>\sans</keyword>
	<keyword>\score</keyword>
	<keyword>\semiflat</keyword>
	<keyword>\semisharp</keyword>
	<keyword>\sesquiflat</keyword>
	<keyword>\sesquisharp</keyword>
	<keyword>\sharp</keyword>
	<keyword>\simple</keyword>
	<keyword>\slashed-digit</keyword>
	<keyword>\small</keyword>
	<keyword>\smallCaps</keyword>
	<keyword>\smaller</keyword>
	<keyword>\stencil</keyword>
	<keyword>\strut</keyword>
	<keyword>\sub</keyword>
	<keyword>\super</keyword>
	<keyword>\teeny</keyword>
	<keyword>\text</keyword>
	<keyword>\tied-lyric</keyword>
	<keyword>\tiny</keyword>
	<keyword>\translate</keyword>
	<keyword>\translate-scaled</keyword>
	<keyword>\transparent</keyword>
	<keyword>\triangle</keyword>
	<keyword>\typewriter</keyword>
	<keyword>\underline</keyword>
	<keyword>\upright</keyword>
	<keyword>\vcenter</keyword>
	<keyword>\verbatim-file</keyword>
	<keyword>\whiteout</keyword>
	<keyword>\with-color</keyword>
	<keyword>\with-dimensions</keyword>
	<keyword>\with-url</keyword>
	<keyword>\wordwrap</keyword>
	<keyword>\wordwrap-field</keyword>
	<keyword>\wordwrap-string</keyword>
   </context>

   <context id="lykeyword" style-ref="lykeyword">
	<keyword>staff-spacing-interface</keyword>
	<keyword>text-script-interface</keyword>
	<keyword>Ottava_spanner_engraver</keyword>
	<keyword>Figured_bass_engraver</keyword>
	<keyword>Dynamic_align_engraver</keyword>
	<keyword>Lyrics</keyword>
	<keyword>Separating_line_group_engraver</keyword>
	<keyword>cluster-interface</keyword>
	<keyword>Glissando_engraver</keyword>
	<keyword>key-signature-interface</keyword>
	<keyword>clef-interface</keyword>
	<keyword>VaticanaVoice</keyword>
	<keyword>Rest_collision_engraver</keyword>
	<keyword>Grace_engraver</keyword>
	<keyword>grid-point-interface</keyword>
	<keyword>Measure_grouping_engraver</keyword>
	<keyword>Laissez_vibrer_engraver</keyword>
	<keyword>Script_row_engraver</keyword>
	<keyword>bass-figure-alignment-interface</keyword>
	<keyword>Note_head_line_engraver</keyword>
	<keyword>ottava-bracket-interface</keyword>
	<keyword>rhythmic-head-interface</keyword>
	<keyword>Accidental_engraver</keyword>
	<keyword>Mark_engraver</keyword>
	<keyword>Instrument_name_engraver</keyword>
	<keyword>Bend_engraver</keyword>
	<keyword>Vaticana_ligature_engraver</keyword>
	<keyword>New_dynamic_engraver</keyword>
	<keyword>Page_turn_engraver</keyword>
	<keyword>staff-symbol-interface</keyword>
	<keyword>Beam_performer</keyword>
	<keyword>accidental-suggestion-interface</keyword>
	<keyword>Key_engraver</keyword>
	<keyword>GrandStaff</keyword>
	<keyword>multi-measure-interface</keyword>
	<keyword>rest-collision-interface</keyword>
	<keyword>Dot_column_engraver</keyword>
	<keyword>MensuralVoice</keyword>
	<keyword>TabStaff</keyword>
	<keyword>Pitched_trill_engraver</keyword>
	<keyword>line-spanner-interface</keyword>
	<keyword>Time_signature_performer</keyword>
	<keyword>percent-repeat-item-interface</keyword>
	<keyword>lyric-interface</keyword>
	<keyword>StaffGroup</keyword>
	<keyword>text-interface</keyword>
	<keyword>slur-interface</keyword>
	<keyword>Drum_note_performer</keyword>
	<keyword>TabVoice</keyword>
	<keyword>measure-grouping-interface</keyword>
	<keyword>stanza-number-interface</keyword>
	<keyword>self-alignment-interface</keyword>
	<keyword>Span_arpeggio_engraver</keyword>
	<keyword>system-interface</keyword>
	<keyword>Engraver</keyword>
	<keyword>RhythmicStaff</keyword>
	<keyword>font-interface</keyword>
	<keyword>fret-diagram-interface</keyword>
	<keyword>Grace_spacing_engraver</keyword>
	<keyword>Bar_engraver</keyword>
	<keyword>unbreakable-spanner-interface</keyword>
	<keyword>Dynamic_engraver</keyword>
	<keyword>Grob_pq_engraver</keyword>
	<keyword>Default_bar_line_engraver</keyword>
	<keyword>Swallow_performer</keyword>
	<keyword>script-column-interface</keyword>
	<keyword>Piano_pedal_performer</keyword>
	<keyword>metronome-mark-interface</keyword>
	<keyword>melody-spanner-interface</keyword>
	<keyword>FretBoards</keyword>
	<keyword>spacing-spanner-interface</keyword>
	<keyword>Control_track_performer</keyword>
	<keyword>Break_align_engraver</keyword>
	<keyword>paper-column-interface</keyword>
	<keyword>PianoStaff</keyword>
	<keyword>Breathing_sign_engraver</keyword>
	<keyword>accidental-placement-interface</keyword>
	<keyword>Tuplet_engraver</keyword>
	<keyword>stroke-finger-interface</keyword>
	<keyword>side-position-interface</keyword>
	<keyword>note-name-interface</keyword>
	<keyword>bar-line-interface</keyword>
	<keyword>lyric-extender-interface</keyword>
	<keyword>Staff</keyword>
	<keyword>GregorianTranscriptionStaff</keyword>
	<keyword>Rest_swallow_translator</keyword>
	<keyword>dynamic-text-spanner-interface</keyword>
	<keyword>arpeggio-interface</keyword>
	<keyword>Cluster_spanner_engraver</keyword>
	<keyword>Collision_engraver</keyword>
	<keyword>accidental-interface</keyword>
	<keyword>rest-interface</keyword>
	<keyword>Tab_note_heads_engraver</keyword>
	<keyword>dots-interface</keyword>
	<keyword>staff-symbol-referencer-interface</keyword>
	<keyword>ambitus-interface</keyword>
	<keyword>bass-figure-interface</keyword>
	<keyword>vaticana-ligature-interface</keyword>
	<keyword>ledgered-interface</keyword>
	<keyword>item-interface</keyword>
	<keyword>Tie_performer</keyword>
	<keyword>volta-bracket-interface</keyword>
	<keyword>vertically-spaceable-interface</keyword>
	<keyword>Chord_tremolo_engraver</keyword>
	<keyword>note-column-interface</keyword>
	<keyword>DrumVoice</keyword>
	<keyword>axis-group-interface</keyword>
	<keyword>Ledger_line_engraver</keyword>
	<keyword>Slash_repeat_engraver</keyword>
	<keyword>ligature-bracket-interface</keyword>
	<keyword>Pitch_squash_engraver</keyword>
	<keyword>Instrument_switch_engraver</keyword>
	<keyword>Voice</keyword>
	<keyword>Script_column_engraver</keyword>
	<keyword>Volta_engraver</keyword>
	<keyword>Stanza_number_align_engraver</keyword>
	<keyword>Vertical_align_engraver</keyword>
	<keyword>span-bar-interface</keyword>
	<keyword>Staff_collecting_engraver</keyword>
	<keyword>Ligature_bracket_engraver</keyword>
	<keyword>Time_signature_engraver</keyword>
	<keyword>Beam_engraver</keyword>
	<keyword>Note_name_engraver</keyword>
	<keyword>Note_heads_engraver</keyword>
	<keyword>Forbid_line_break_engraver</keyword>
	<keyword>spacing-options-interface</keyword>
	<keyword>spacing-interface</keyword>
	<keyword>piano-pedal-script-interface</keyword>
	<keyword>MensuralStaff</keyword>
	<keyword>Global</keyword>
	<keyword>trill-pitch-accidental-interface</keyword>
	<keyword>grob-interface</keyword>
	<keyword>Horizontal_bracket_engraver</keyword>
	<keyword>Grid_line_span_engraver</keyword>
	<keyword>NoteNames</keyword>
	<keyword>piano-pedal-interface</keyword>
	<keyword>Axis_group_engraver</keyword>
	<keyword>Staff_symbol_engraver</keyword>
	<keyword>stem-interface</keyword>
	<keyword>Note_spacing_engraver</keyword>
	<keyword>Slur_engraver</keyword>
	<keyword>pitched-trill-interface</keyword>
	<keyword>tie-column-interface</keyword>
	<keyword>stem-tremolo-interface</keyword>
	<keyword>Grid_point_engraver</keyword>
	<keyword>System_start_delimiter_engraver</keyword>
	<keyword>Completion_heads_engraver</keyword>
	<keyword>Drum_notes_engraver</keyword>
	<keyword>Swallow_engraver</keyword>
	<keyword>Slur_performer</keyword>
	<keyword>ledger-line-spanner-interface</keyword>
	<keyword>key-cancellation-interface</keyword>
	<keyword>lyric-hyphen-interface</keyword>
	<keyword>Clef_engraver</keyword>
	<keyword>dynamic-interface</keyword>
	<keyword>Score</keyword>
	<keyword>Output_property_engraver</keyword>
	<keyword>Repeat_tie_engraver</keyword>
	<keyword>Rest_engraver</keyword>
	<keyword>break-aligned-interface</keyword>
	<keyword>String_number_engraver</keyword>
	<keyword>only-prebreak-interface</keyword>
	<keyword>Lyric_engraver</keyword>
	<keyword>Tempo_performer</keyword>
	<keyword>Parenthesis_engraver</keyword>
	<keyword>Repeat_acknowledge_engraver</keyword>
	<keyword>mensural-ligature-interface</keyword>
	<keyword>align-interface</keyword>
	<keyword>Stanza_number_engraver</keyword>
	<keyword>system-start-delimiter-interface</keyword>
	<keyword>lyric-syllable-interface</keyword>
	<keyword>bend-after-interface</keyword>
	<keyword>dynamic-line-spanner-interface</keyword>
	<keyword>Staff_performer</keyword>
	<keyword>Bar_number_engraver</keyword>
	<keyword>Fretboard_engraver</keyword>
	<keyword>tablature-interface</keyword>
	<keyword>Fingering_engraver</keyword>
	<keyword>chord-name-interface</keyword>
	<keyword>Note_swallow_translator</keyword>
	<keyword>Chord_name_engraver</keyword>
	<keyword>note-head-interface</keyword>
	<keyword>breathing-sign-interface</keyword>
	<keyword>Extender_engraver</keyword>
	<keyword>Ambitus_engraver</keyword>
	<keyword>DrumStaff</keyword>
	<keyword>dot-column-interface</keyword>
	<keyword>Lyric_performer</keyword>
	<keyword>enclosing-bracket-interface</keyword>
	<keyword>Trill_spanner_engraver</keyword>
	<keyword>Key_performer</keyword>
	<keyword>hairpin-interface</keyword>
	<keyword>Vertically_spaced_contexts_engraver</keyword>
	<keyword>Hyphen_engraver</keyword>
	<keyword>Dots_engraver</keyword>
	<keyword>multi-measure-rest-interface</keyword>
	<keyword>Multi_measure_rest_engraver</keyword>
	<keyword>Grace_beam_engraver</keyword>
	<keyword>separation-item-interface</keyword>
	<keyword>instrument-specific-markup-interface</keyword>
	<keyword>Balloon_engraver</keyword>
	<keyword>Translator</keyword>
	<keyword>Tweak_engraver</keyword>
	<keyword>Devnull</keyword>
	<keyword>Spacing_engraver</keyword>
	<keyword>Piano_pedal_align_engraver</keyword>
	<keyword>system-start-text-interface</keyword>
	<keyword>parentheses-interface</keyword>
	<keyword>ChoirStaff</keyword>
	<keyword>Span_bar_engraver</keyword>
	<keyword>Text_engraver</keyword>
	<keyword>GregorianTranscriptionVoice</keyword>
	<keyword>Timing_translator</keyword>
	<keyword>script-interface</keyword>
	<keyword>semi-tie-interface</keyword>
	<keyword>Percent_repeat_engraver</keyword>
	<keyword>break-alignable-interface</keyword>
	<keyword>Tab_staff_symbol_engraver</keyword>
	<keyword>line-interface</keyword>
	<keyword>rhythmic-grob-interface</keyword>
	<keyword>Dynamic_performer</keyword>
	<keyword>note-spacing-interface</keyword>
	<keyword>spanner-interface</keyword>
	<keyword>break-alignment-interface</keyword>
	<keyword>tuplet-number-interface</keyword>
	<keyword>Rhythmic_column_engraver</keyword>
	<keyword>cluster-beacon-interface</keyword>
	<keyword>horizontal-bracket-interface</keyword>
	<keyword>Mensural_ligature_engraver</keyword>
	<keyword>ChordNames</keyword>
	<keyword>gregorian-ligature-interface</keyword>
	<keyword>Melody_engraver</keyword>
	<keyword>ligature-interface</keyword>
	<keyword>Paper_column_engraver</keyword>
	<keyword>FiguredBass</keyword>
	<keyword>grace-spacing-interface</keyword>
	<keyword>tie-interface</keyword>
	<keyword>New_fingering_engraver</keyword>
	<keyword>Script_engraver</keyword>
	<keyword>Metronome_mark_engraver</keyword>
	<keyword>Tab_harmonic_engraver</keyword>
	<keyword>hara-kiri-group-spanner-interface</keyword>
	<keyword>string-number-interface</keyword>
	<keyword>Hara_kiri_engraver</keyword>
	<keyword>grid-line-interface</keyword>
	<keyword>Skip_event_swallow_translator</keyword>
	<keyword>Auto_beam_engraver</keyword>
	<keyword>balloon-interface</keyword>
	<keyword>spaceable-grob-interface</keyword>
	<keyword>trill-spanner-interface</keyword>
	<keyword>Font_size_engraver</keyword>
	<keyword>figured-bass-continuation-interface</keyword>
	<keyword>semi-tie-column-interface</keyword>
	<keyword>CueVoice</keyword>
	<keyword>Phrasing_slur_engraver</keyword>
	<keyword>Arpeggio_engraver</keyword>
	<keyword>mark-interface</keyword>
	<keyword>VaticanaStaff</keyword>
	<keyword>piano-pedal-bracket-interface</keyword>
	<keyword>beam-interface</keyword>
	<keyword>Note_performer</keyword>
	<keyword>custos-interface</keyword>
	<keyword>percent-repeat-interface</keyword>
	<keyword>time-signature-interface</keyword>
	<keyword>Custos_engraver</keyword>
	<keyword>Part_combine_engraver</keyword>
	<keyword>Piano_pedal_engraver</keyword>
	<keyword>tuplet-bracket-interface</keyword>
	<keyword>Stem_engraver</keyword>
	<keyword>finger-interface</keyword>
	<keyword>note-collision-interface</keyword>
	<keyword>Spanner_break_forbid_engraver</keyword>
	<keyword>Text_spanner_engraver</keyword>
	<keyword>Tie_engraver</keyword>
	<keyword>Figured_bass_position_engraver</keyword>
   </context>

    <context id="ly">
      <include>
        <context ref="line-command"/>
        <context ref="comment"/>
      </include>
    </context>

  </definitions>
</language>

```

And this is what I added to classic.xml:
```
  
  <style name="ly:quotation"               foreground="purple" />
  <style name="ly:octave"		   foreground="red" />
  <style name="ly:mensural-notation"	   foreground="violet" />
  <style name="ly:internal-commands"	   foreground="orange" />
  <style name="ly:music-functions"	   foreground="cyan" />
  <style name="ly:markup-commands"	   foreground="cyan" />
  <style name="ly:lykeyword"		   foreground="green" />

```

Can someone help me to get it to work? :)

---

### Post by ibuclaw on 2009-05-10
Running gedit in a terminal will point you in the right direction ;)

```

iain@jstdio:~$ gedit 

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:quotation' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'def:line-comment' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:octave' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:brackets' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:mensural-notation' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:internal-commands' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:music-functions' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:markup-commands' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:identifiers' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:lykeyword' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:error' not defined

(gedit:15163): GtkSourceView-WARNING **: in file /usr/share/gtksourceview-2.0/language-specs/lilypond.lang: style 'lilypond:error' not defined

(gedit:15163): GtkSourceView-WARNING **: Failed to load '/usr/share/gtksourceview-2.0/language-specs/lilypond.lang': Error while compiling regular expression (?-ix)\b(reve|\longa|\maxima)\b at char 15: case-changing escapes (\l, \L, \u, \U) are not allowed here

```

On this line:
```
<keyword>\longa</keyword>
```
Perhaps it should be:
```
<keyword>longa</keyword>
<keyword>Longa</keyword>
```
Although, there will most likely be a few more tweaks than that to do in order to get it working...

Regards
Iain

---

### Post by Eider on 2009-05-11
Thank you very much for your help!
I've made some changes and ran gedit in a terminal.
I didn't get any errors.

My new Lilypond.lang file:
I've removed the \ and replaced it with <prefix>\\</prefix>
```
<?xml version="1.0" encoding="UTF-8"?>


<language id="ly" _name="Lilypond" version="1.0" _section="Others">
  <metadata>
    <property name="mimetypes">text/x-lilypond</property>
    <property name="globs">*.ly</property>
    <property name="block-comment-start">%{</property>
    <property name="block-comment-end">%}</property>
    <property name="line-comment-start">%</property>
  </metadata>

  <styles>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="quotation" _name="Quotation" map-to="ly:quotation"/>
    <style id="line-comment" _name="Line Comment" map-to="def:comment"/>
    <style id="octave" _name="Octave" map-to="ly:octave"/>
    <style id="brackets" _name="Brackets" map-to="ly:brackets"/>
    <style id="mensural-notation" _name="Mensural Notation" map-to="ly:mensural-notation"/>
    <style id="internal-commands" _name="Internal Commands" map-to="ly:internal-commands"/>
    <style id="music-functions" _name="Music Functions" map-to="ly:music-functions"/>
    <style id="markup-commands" _name="Markup Commands" map-to="ly:markup-commands"/>
    <style id="identifiers" _name="Identifiers" map-to="ly:identifiers"/>
    <style id="lykeyword" _name="Keywords" map-to="ly:lykeyword"/>
  </styles>

  <definitions>

    <context id="comment" style-ref="comment">
      <start>%{</start>
      <end>%}</end>
      <include>
        <context style-ref="error" extend-parent="false">
          <match>%{</match>
        </context>
        <context ref="def:in-comment"/>
      </include>
    </context>

    <context id="quotation" style-ref="quotation">
      <start>"</start>
      <end>"</end>
      <include>
        <context style-ref="error" extend-parent="false">
          <match>"</match>
        </context>
        <context ref="def:quotation"/>
      </include>
    </context>

    <context id="line-comment" style-ref="comment" end-at-line-end="true" extend-parent="false">
      <start>%</start>
      <include>
        <context ref="def:line-comment"/>
      </include>
    </context>

   <context id="octave" style-ref="octave">
	<keyword>,</keyword>
	<keyword>'</keyword>
   </context>

   <context id="brackets" style-ref="internal-commands">
	<keyword>{</keyword>
	<keyword>}</keyword>
	<keyword>[</keyword>
	<keyword>]</keyword>
	<keyword>&lt;&lt;</keyword>
	<keyword>&gt;&gt;</keyword>
   </context>

   <context id="mensural-notation" style-ref="mensural-notation">
    <prefix>\\</prefix>
	<keyword>reve</keyword>
	<keyword>longa</keyword>
	<keyword>maxima</keyword>
   </context>

   <context id="internal-commands" style-ref="internal-commands">
    <prefix>\\</prefix>
	<keyword>override</keyword>
	<keyword>version</keyword>
	<keyword>include</keyword>
	<keyword>invalid</keyword>
	<keyword>addquote</keyword>
	<keyword>alternative</keyword>
	<keyword>book</keyword>
	<keyword>~</keyword>
	<keyword>mark</keyword>
	<keyword>default</keyword>
	<keyword>key</keyword>
	<keyword>skip</keyword>
	<keyword>octave</keyword>
	<keyword>partial</keyword>
	<keyword>time</keyword>
	<keyword>change</keyword>
	<keyword>consists</keyword>
	<keyword>remove</keyword>
	<keyword>accepts</keyword>
	<keyword>defaultchild</keyword>
	<keyword>denies</keyword>
	<keyword>alias</keyword>
	<keyword>type</keyword>
	<keyword>description</keyword>
	<keyword>name</keyword>
	<keyword>context</keyword>
	<keyword>grobdescriptions</keyword>
	<keyword>markup</keyword>
	<keyword>header</keyword>
	<keyword>notemode</keyword>
	<keyword>drummode</keyword>
	<keyword>figuremode</keyword>
	<keyword>chordmode</keyword>
	<keyword>lyricmode</keyword>
	<keyword>drums</keyword>
	<keyword>figures</keyword>
	<keyword>chords</keyword>
	<keyword>lyrics</keyword>
	<keyword>once</keyword>
	<keyword>revert</keyword>
	<keyword>set</keyword>
	<keyword>unset</keyword>
	<keyword>addlyrics</keyword>
	<keyword>objectid</keyword>
	<keyword>with</keyword>
	<keyword>rest</keyword>
	<keyword>paper</keyword>
	<keyword>midi</keyword>
	<keyword>layout</keyword>
	<keyword>new</keyword>
	<keyword>times</keyword>
	<keyword>transpose</keyword>
	<keyword>tag</keyword>
	<keyword>relative</keyword>
	<keyword>renameinput</keyword>
	<keyword>repeat</keyword>
	<keyword>lyricsto</keyword>
	<keyword>score</keyword>
	<keyword>sequential</keyword>
	<keyword>simultaneous</keyword>
	<keyword>longa</keyword>
	<keyword>breve</keyword>
	<keyword>maxima</keyword>
	<keyword>tempo</keyword>
   </context>

   <context id="identifiers" style-ref="identifiers">
    <prefix>\\</prefix>
	<keyword>override</keyword>
	<keyword>version</keyword>
	<keyword>include</keyword>
	<keyword>invalid</keyword>
	<keyword>addquote</keyword>
	<keyword>alternative</keyword>
	<keyword>book</keyword>
	<keyword>~</keyword>
	<keyword>mark</keyword>
	<keyword>default</keyword>
	<keyword>key</keyword>
	<keyword>skip</keyword>
	<keyword>octave</keyword>
	<keyword>partial</keyword>
	<keyword>time</keyword>
	<keyword>change</keyword>
	<keyword>consists</keyword>
	<keyword>remove</keyword>
	<keyword>accepts</keyword>
	<keyword>defaultchild</keyword>
	<keyword>denies</keyword>
	<keyword>alias</keyword>
	<keyword>type</keyword>
	<keyword>description</keyword>
	<keyword>name</keyword>
	<keyword>context</keyword>
	<keyword>grobdescriptions</keyword>
	<keyword>markup</keyword>
	<keyword>header</keyword>
	<keyword>notemode</keyword>
	<keyword>drummode</keyword>
	<keyword>figuremode</keyword>
	<keyword>chordmode</keyword>
	<keyword>lyricmode</keyword>
	<keyword>drums</keyword>
	<keyword>figures</keyword>
	<keyword>chords</keyword>
	<keyword>lyrics</keyword>
	<keyword>once</keyword>
	<keyword>revert</keyword>
	<keyword>set</keyword>
	<keyword>unset</keyword>
	<keyword>addlyrics</keyword>
	<keyword>objectid</keyword>
	<keyword>with</keyword>
	<keyword>rest</keyword>
	<keyword>paper</keyword>
	<keyword>midi</keyword>
	<keyword>layout</keyword>
	<keyword>new</keyword>
	<keyword>times</keyword>
	<keyword>transpose</keyword>
	<keyword>tag</keyword>
	<keyword>relative</keyword>
	<keyword>renameinput</keyword>
	<keyword>repeat</keyword>
	<keyword>lyricsto</keyword>
	<keyword>score</keyword>
	<keyword>sequential</keyword>
	<keyword>simultaneous</keyword>
	<keyword>longa</keyword>
	<keyword>breve</keyword>
	<keyword>maxima</keyword>
	<keyword>tempo</keyword>
	<keyword>AncientRemoveEmptyStaffContext</keyword>
	<keyword>RemoveEmptyRhythmicStaffContext</keyword>
	<keyword>RemoveEmptyStaffContext</keyword>
	<keyword>accent</keyword>
	<keyword>aeolian</keyword>
	<keyword>afterGraceFraction</keyword>
	<keyword>aikenHeads</keyword>
	<keyword>arpeggio</keyword>
	<keyword>arpeggioArrowDown</keyword>
	<keyword>arpeggioArrowUp</keyword>
	<keyword>arpeggioBracket</keyword>
	<keyword>arpeggioNormal</keyword>
	<keyword>arpeggioParenthesis</keyword>
	<keyword>autoBeamOff</keyword>
	<keyword>autoBeamOn</keyword>
	<keyword>balloonLengthOff</keyword>
	<keyword>balloonLengthOn</keyword>
	<keyword>bassFigureExtendersOff</keyword>
	<keyword>bassFigureExtendersOn</keyword>
	<keyword>bassFigureStaffAlignmentDown</keyword>
	<keyword>bassFigureStaffAlignmentNeutral</keyword>
	<keyword>bassFigureStaffAlignmentUp</keyword>
	<keyword>between-system-padding</keyword>
	<keyword>between-system-space</keyword>
	<keyword>bigger</keyword>
	<keyword>blackTriangleMarkup</keyword>
	<keyword>bookTitleMarkup</keyword>
	<keyword>bracketCloseSymbol</keyword>
	<keyword>bracketOpenSymbol</keyword>
	<keyword>break</keyword>
	<keyword>breve</keyword>
	<keyword>cadenzaOff</keyword>
	<keyword>cadenzaOn</keyword>
	<keyword>center</keyword>
	<keyword>chordmodifiers</keyword>
	<keyword>cm</keyword>
	<keyword>coda</keyword>
	<keyword>compressFullBarRests</keyword>
	<keyword>cr</keyword>
	<keyword>cresc</keyword>
	<keyword>crescHairpin</keyword>
	<keyword>crescTextCresc</keyword>
	<keyword>decr</keyword>
	<keyword>defaultTimeSignature</keyword>
	<keyword>dim</keyword>
	<keyword>dimHairpin</keyword>
	<keyword>dimTextDecr</keyword>
	<keyword>dimTextDecresc</keyword>
	<keyword>dimTextDim</keyword>
	<keyword>dorian</keyword>
	<keyword>dotsDown</keyword>
	<keyword>dotsNeutral</keyword>
	<keyword>dotsUp</keyword>
	<keyword>down</keyword>
	<keyword>downbow</keyword>
	<keyword>downmordent</keyword>
	<keyword>downprall</keyword>
	<keyword>drumPitchNames</keyword>
	<keyword>dutchPitchnames</keyword>
	<keyword>dynamicDown</keyword>
	<keyword>dynamicNeutral</keyword>
	<keyword>dynamicUp</keyword>
	<keyword>easyHeadsOff</keyword>
	<keyword>easyHeadsOn</keyword>
	<keyword>endcr</keyword>
	<keyword>endcresc</keyword>
	<keyword>enddecr</keyword>
	<keyword>enddim</keyword>
	<keyword>endincipit</keyword>
	<keyword>escapedBiggerSymbol</keyword>
	<keyword>escapedExclamationSymbol</keyword>
	<keyword>escapedParenthesisCloseSymbol</keyword>
	<keyword>escapedParenthesisOpenSymbol</keyword>
	<keyword>escapedSmallerSymbol</keyword>
	<keyword>espressivo</keyword>
	<keyword>evenHeaderMarkup</keyword>
	<keyword>expandFullBarRests</keyword>
	<keyword>f</keyword>
	<keyword>fermata</keyword>
	<keyword>fermataMarkup</keyword>
	<keyword>ff</keyword>
	<keyword>fff</keyword>
	<keyword>ffff</keyword>
	<keyword>first-page-number</keyword>
	<keyword>flageolet</keyword>
	<keyword>fp</keyword>
	<keyword>frenchChords</keyword>
	<keyword>fullJazzExceptions</keyword>
	<keyword>fz</keyword>
	<keyword>germanChords</keyword>
	<keyword>glissando</keyword>
	<keyword>harmonic</keyword>
	<keyword>hideNotes</keyword>
	<keyword>hideStaffSwitch</keyword>
	<keyword>huge</keyword>
	<keyword>ignatzekExceptionMusic</keyword>
	<keyword>ignatzekExceptions</keyword>
	<keyword>improvisationOff</keyword>
	<keyword>improvisationOn</keyword>
	<keyword>in</keyword>
	<keyword>instrument-definitions</keyword>
	<keyword>ionian</keyword>
	<keyword>italianChords</keyword>
	<keyword>laissezVibrer</keyword>
	<keyword>large</keyword>
	<keyword>left</keyword>
	<keyword>lheel</keyword>
	<keyword>lineprall</keyword>
	<keyword>locrian</keyword>
	<keyword>longa</keyword>
	<keyword>longfermata</keyword>
	<keyword>ltoe</keyword>
	<keyword>lydian</keyword>
	<keyword>major</keyword>
	<keyword>marcato</keyword>
	<keyword>maxima</keyword>
	<keyword>melisma</keyword>
	<keyword>melismaEnd</keyword>
	<keyword>mergeDifferentlyDottedOff</keyword>
	<keyword>mergeDifferentlyDottedOn</keyword>
	<keyword>mergeDifferentlyHeadedOff</keyword>
	<keyword>mergeDifferentlyHeadedOn</keyword>
	<keyword>mf</keyword>
	<keyword>midiDrumPitches</keyword>
	<keyword>minor</keyword>
	<keyword>mixolydian</keyword>
	<keyword>mm</keyword>
	<keyword>mordent</keyword>
	<keyword>mp</keyword>
	<keyword>newSpacingSection</keyword>
	<keyword>noBeam</keyword>
	<keyword>noBreak</keyword>
	<keyword>normalsize</keyword>
	<keyword>numericTimeSignature</keyword>
	<keyword>oddFooterMarkup</keyword>
	<keyword>oddHeaderMarkup</keyword>
	<keyword>oneVoice</keyword>
	<keyword>open</keyword>
	<keyword>output-scale</keyword>
	<keyword>p</keyword>
	<keyword>page-limit-inter-system-space</keyword>
	<keyword>page-top-space</keyword>
	<keyword>parenthesisCloseSymbol</keyword>
	<keyword>parenthesisOpenSymbol</keyword>
	<keyword>partialJazzExceptions</keyword>
	<keyword>partialJazzMusic</keyword>
	<keyword>phrasingSlurDashed</keyword>
	<keyword>phrasingSlurDotted</keyword>
	<keyword>phrasingSlurDown</keyword>
	<keyword>phrasingSlurNeutral</keyword>
	<keyword>phrasingSlurSolid</keyword>
	<keyword>phrasingSlurUp</keyword>
	<keyword>phrygian</keyword>
	<keyword>pipeSymbol</keyword>
	<keyword>pitchnames</keyword>
	<keyword>portato</keyword>
	<keyword>pp</keyword>
	<keyword>ppp</keyword>
	<keyword>pppp</keyword>
	<keyword>ppppp</keyword>
	<keyword>prall</keyword>
	<keyword>pralldown</keyword>
	<keyword>prallmordent</keyword>
	<keyword>prallprall</keyword>
	<keyword>prallup</keyword>
	<keyword>predefinedFretboardsOff</keyword>
	<keyword>predefinedFretboardsOn</keyword>
	<keyword>print-first-page-number</keyword>
	<keyword>print-page-number</keyword>
	<keyword>pt</keyword>
	<keyword>ragged-bottom</keyword>
	<keyword>ragged-last-bottom</keyword>
	<keyword>repeatTie</keyword>
	<keyword>reverseturn</keyword>
	<keyword>rfz</keyword>
	<keyword>rheel</keyword>
	<keyword>right</keyword>
	<keyword>rtoe</keyword>
	<keyword>sacredHarpHeads</keyword>
	<keyword>scoreTitleMarkup</keyword>
	<keyword>segno</keyword>
	<keyword>semiGermanChords</keyword>
	<keyword>setDefaultDurationToQuarter</keyword>
	<keyword>sf</keyword>
	<keyword>sff</keyword>
	<keyword>sfp</keyword>
	<keyword>sfz</keyword>
	<keyword>shiftOff</keyword>
	<keyword>shiftOn</keyword>
	<keyword>shiftOnn</keyword>
	<keyword>shiftOnnn</keyword>
	<keyword>shortfermata</keyword>
	<keyword>showStaffSwitch</keyword>
	<keyword>signumcongruentiae</keyword>
	<keyword>slashSeparator</keyword>
	<keyword>slurDashed</keyword>
	<keyword>slurDotted</keyword>
	<keyword>slurDown</keyword>
	<keyword>slurNeutral</keyword>
	<keyword>slurSolid</keyword>
	<keyword>slurUp</keyword>
	<keyword>small</keyword>
	<keyword>smaller</keyword>
	<keyword>sostenutoOff</keyword>
	<keyword>sostenutoOn</keyword>
	<keyword>sp</keyword>
	<keyword>spp</keyword>
	<keyword>staccatissimo</keyword>
	<keyword>staccato</keyword>
	<keyword>start</keyword>
	<keyword>startAcciaccaturaMusic</keyword>
	<keyword>startAppoggiaturaMusic</keyword>
	<keyword>startGraceMusic</keyword>
	<keyword>startGroup</keyword>
	<keyword>startStaff</keyword>
	<keyword>startTextSpan</keyword>
	<keyword>startTrillSpan</keyword>
	<keyword>stemDown</keyword>
	<keyword>stemNeutral</keyword>
	<keyword>stemUp</keyword>
	<keyword>stop</keyword>
	<keyword>stopAcciaccaturaMusic</keyword>
	<keyword>stopAppoggiaturaMusic</keyword>
	<keyword>stopGraceMusic</keyword>
	<keyword>stopGroup</keyword>
	<keyword>stopStaff</keyword>
	<keyword>stopTextSpan</keyword>
	<keyword>stopTrillSpan</keyword>
	<keyword>stopped</keyword>
	<keyword>sustainOff</keyword>
	<keyword>sustainOn</keyword>
	<keyword>tagline</keyword>
	<keyword>teeny</keyword>
	<keyword>tenuto</keyword>
	<keyword>textLengthOff</keyword>
	<keyword>textLengthOn</keyword>
	<keyword>textSpannerDown</keyword>
	<keyword>textSpannerNeutral</keyword>
	<keyword>textSpannerUp</keyword>
	<keyword>thumb</keyword>
	<keyword>tieDashed</keyword>
	<keyword>tieDotted</keyword>
	<keyword>tieDown</keyword>
	<keyword>tieNeutral</keyword>
	<keyword>tieSolid</keyword>
	<keyword>tieUp</keyword>
	<keyword>tildeSymbol</keyword>
	<keyword>tiny</keyword>
	<keyword>tocItemMarkup</keyword>
	<keyword>tocTitleMarkup</keyword>
	<keyword>treCorde</keyword>
	<keyword>trill</keyword>
	<keyword>tupletDown</keyword>
	<keyword>tupletNeutral</keyword>
	<keyword>tupletUp</keyword>
	<keyword>turn</keyword>
	<keyword>unHideNotes</keyword>
	<keyword>unaCorda</keyword>
	<keyword>unit</keyword>
	<keyword>up</keyword>
	<keyword>upbow</keyword>
	<keyword>upmordent</keyword>
	<keyword>upprall</keyword>
	<keyword>varcoda</keyword>
	<keyword>verylongfermata</keyword>
	<keyword>voiceFour</keyword>
	<keyword>voiceFourStyle</keyword>
	<keyword>voiceNeutralStyle</keyword>
	<keyword>voiceOne</keyword>
	<keyword>voiceOneStyle</keyword>
	<keyword>voiceThree</keyword>
	<keyword>voiceThreeStyle</keyword>
	<keyword>voiceTwo</keyword>
	<keyword>voiceTwoStyle</keyword>
	<keyword>whiteTriangleMarkup</keyword>
   </context>

   <context id="music-functions" style-ref="music-functions">
    <prefix>\\</prefix>
	<keyword>acciaccatura</keyword>
	<keyword>addChordShape</keyword>
	<keyword>addInstrumentDefinition</keyword>
	<keyword>addQuote</keyword>
	<keyword>afterGrace</keyword>
	<keyword>allowPageTurn</keyword>
	<keyword>applyContext</keyword>
	<keyword>applyMusic</keyword>
	<keyword>applyOutput</keyword>
	<keyword>appoggiatura</keyword>
	<keyword>assertBeamQuant</keyword>
	<keyword>assertBeamSlope</keyword>
	<keyword>autochange</keyword>
	<keyword>balloonGrobText</keyword>
	<keyword>balloonText</keyword>
	<keyword>bar</keyword>
	<keyword>barNumberCheck</keyword>
	<keyword>bendAfter</keyword>
	<keyword>breathe</keyword>
	<keyword>clef</keyword>
	<keyword>cueDuring</keyword>
	<keyword>displayLilyMusic</keyword>
	<keyword>displayMusic</keyword>
	<keyword>endSpanners</keyword>
	<keyword>featherDurations</keyword>
	<keyword>grace</keyword>
	<keyword>includePageLayoutFile</keyword>
	<keyword>instrumentSwitch</keyword>
	<keyword>keepWithTag</keyword>
	<keyword>killCues</keyword>
	<keyword>label</keyword>
	<keyword>makeClusters</keyword>
	<keyword>musicMap</keyword>
	<keyword>noPageBreak</keyword>
	<keyword>noPageTurn</keyword>
	<keyword>octaveCheck</keyword>
	<keyword>oldaddlyrics</keyword>
	<keyword>ottava</keyword>
	<keyword>overrideProperty</keyword>
	<keyword>pageBreak</keyword>
	<keyword>pageTurn</keyword>
	<keyword>parallelMusic</keyword>
	<keyword>parenthesize</keyword>
	<keyword>partcombine</keyword>
	<keyword>pitchedTrill</keyword>
	<keyword>pointAndClickOff</keyword>
	<keyword>pointAndClickOn</keyword>
	<keyword>quoteDuring</keyword>
	<keyword>removeWithTag</keyword>
	<keyword>resetRelativeOctave</keyword>
	<keyword>rightHandFinger</keyword>
	<keyword>scaleDurations</keyword>
	<keyword>scoreTweak</keyword>
	<keyword>shiftDurations</keyword>
	<keyword>spacingTweaks</keyword>
	<keyword>storePredefinedDiagram</keyword>
	<keyword>tag</keyword>
	<keyword>tocItem</keyword>
	<keyword>transposedCueDuring</keyword>
	<keyword>transposition</keyword>
	<keyword>tweak</keyword>
	<keyword>unfoldRepeats</keyword>
	<keyword>withMusicProperty</keyword>
   </context>

   <context id="markup-commands" style-ref="markup-commands">
    <prefix>\\</prefix>
	<keyword>abs-fontsize</keyword>
	<keyword>arrow-head</keyword>
	<keyword>backslashed-digit</keyword>
	<keyword>beam</keyword>
	<keyword>bold</keyword>
	<keyword>box</keyword>
	<keyword>bracket</keyword>
	<keyword>caps</keyword>
	<keyword>center-align</keyword>
	<keyword>center-column</keyword>
	<keyword>char</keyword>
	<keyword>circle</keyword>
	<keyword>column</keyword>
	<keyword>combine</keyword>
	<keyword>concat</keyword>
	<keyword>dir-column</keyword>
	<keyword>doubleflat</keyword>
	<keyword>doublesharp</keyword>
	<keyword>draw-circle</keyword>
	<keyword>draw-line</keyword>
	<keyword>dynamic</keyword>
	<keyword>epsfile</keyword>
	<keyword>fill-line</keyword>
	<keyword>filled-box</keyword>
	<keyword>finger</keyword>
	<keyword>flat</keyword>
	<keyword>fontCaps</keyword>
	<keyword>fontsize</keyword>
	<keyword>fraction</keyword>
	<keyword>fret-diagram</keyword>
	<keyword>fret-diagram-terse</keyword>
	<keyword>fret-diagram-verbose</keyword>
	<keyword>fromproperty</keyword>
	<keyword>general-align</keyword>
	<keyword>halign</keyword>
	<keyword>harp-pedal</keyword>
	<keyword>hbracket</keyword>
	<keyword>hcenter-in</keyword>
	<keyword>hspace</keyword>
	<keyword>huge</keyword>
	<keyword>italic</keyword>
	<keyword>justify</keyword>
	<keyword>justify-field</keyword>
	<keyword>justify-string</keyword>
	<keyword>large</keyword>
	<keyword>larger</keyword>
	<keyword>left-align</keyword>
	<keyword>left-column</keyword>
	<keyword>line</keyword>
	<keyword>lookup</keyword>
	<keyword>lower</keyword>
	<keyword>magnify</keyword>
	<keyword>markalphabet</keyword>
	<keyword>markletter</keyword>
	<keyword>medium</keyword>
	<keyword>musicglyph</keyword>
	<keyword>natural</keyword>
	<keyword>normal-size-sub</keyword>
	<keyword>normal-size-super</keyword>
	<keyword>normal-text</keyword>
	<keyword>normalsize</keyword>
	<keyword>note</keyword>
	<keyword>note-by-number</keyword>
	<keyword>null</keyword>
	<keyword>number</keyword>
	<keyword>on-the-fly</keyword>
	<keyword>override</keyword>
	<keyword>pad-around</keyword>
	<keyword>pad-markup</keyword>
	<keyword>pad-to-box</keyword>
	<keyword>pad-x</keyword>
	<keyword>page-ref</keyword>
	<keyword>postscript</keyword>
	<keyword>put-adjacent</keyword>
	<keyword>raise</keyword>
	<keyword>right-align</keyword>
	<keyword>right-column</keyword>
	<keyword>roman</keyword>
	<keyword>rotate</keyword>
	<keyword>rounded-box</keyword>
	<keyword>sans</keyword>
	<keyword>score</keyword>
	<keyword>semiflat</keyword>
	<keyword>semisharp</keyword>
	<keyword>sesquiflat</keyword>
	<keyword>sesquisharp</keyword>
	<keyword>sharp</keyword>
	<keyword>simple</keyword>
	<keyword>slashed-digit</keyword>
	<keyword>small</keyword>
	<keyword>smallCaps</keyword>
	<keyword>smaller</keyword>
	<keyword>stencil</keyword>
	<keyword>strut</keyword>
	<keyword>sub</keyword>
	<keyword>super</keyword>
	<keyword>teeny</keyword>
	<keyword>text</keyword>
	<keyword>tied-lyric</keyword>
	<keyword>tiny</keyword>
	<keyword>translate</keyword>
	<keyword>translate-scaled</keyword>
	<keyword>transparent</keyword>
	<keyword>triangle</keyword>
	<keyword>typewriter</keyword>
	<keyword>underline</keyword>
	<keyword>upright</keyword>
	<keyword>vcenter</keyword>
	<keyword>verbatim-file</keyword>
	<keyword>whiteout</keyword>
	<keyword>with-color</keyword>
	<keyword>with-dimensions</keyword>
	<keyword>with-url</keyword>
	<keyword>wordwrap</keyword>
	<keyword>wordwrap-field</keyword>
	<keyword>wordwrap-string</keyword>
   </context>

   <context id="lykeyword" style-ref="lykeyword">
    <prefix>\\</prefix>
	<keyword>staff-spacing-interface</keyword>
	<keyword>text-script-interface</keyword>
	<keyword>Ottava_spanner_engraver</keyword>
	<keyword>Figured_bass_engraver</keyword>
	<keyword>Dynamic_align_engraver</keyword>
	<keyword>Lyrics</keyword>
	<keyword>Separating_line_group_engraver</keyword>
	<keyword>cluster-interface</keyword>
	<keyword>Glissando_engraver</keyword>
	<keyword>key-signature-interface</keyword>
	<keyword>clef-interface</keyword>
	<keyword>VaticanaVoice</keyword>
	<keyword>Rest_collision_engraver</keyword>
	<keyword>Grace_engraver</keyword>
	<keyword>grid-point-interface</keyword>
	<keyword>Measure_grouping_engraver</keyword>
	<keyword>Laissez_vibrer_engraver</keyword>
	<keyword>Script_row_engraver</keyword>
	<keyword>bass-figure-alignment-interface</keyword>
	<keyword>Note_head_line_engraver</keyword>
	<keyword>ottava-bracket-interface</keyword>
	<keyword>rhythmic-head-interface</keyword>
	<keyword>Accidental_engraver</keyword>
	<keyword>Mark_engraver</keyword>
	<keyword>Instrument_name_engraver</keyword>
	<keyword>Bend_engraver</keyword>
	<keyword>Vaticana_ligature_engraver</keyword>
	<keyword>New_dynamic_engraver</keyword>
	<keyword>Page_turn_engraver</keyword>
	<keyword>staff-symbol-interface</keyword>
	<keyword>Beam_performer</keyword>
	<keyword>accidental-suggestion-interface</keyword>
	<keyword>Key_engraver</keyword>
	<keyword>GrandStaff</keyword>
	<keyword>multi-measure-interface</keyword>
	<keyword>rest-collision-interface</keyword>
	<keyword>Dot_column_engraver</keyword>
	<keyword>MensuralVoice</keyword>
	<keyword>TabStaff</keyword>
	<keyword>Pitched_trill_engraver</keyword>
	<keyword>line-spanner-interface</keyword>
	<keyword>Time_signature_performer</keyword>
	<keyword>percent-repeat-item-interface</keyword>
	<keyword>lyric-interface</keyword>
	<keyword>StaffGroup</keyword>
	<keyword>text-interface</keyword>
	<keyword>slur-interface</keyword>
	<keyword>Drum_note_performer</keyword>
	<keyword>TabVoice</keyword>
	<keyword>measure-grouping-interface</keyword>
	<keyword>stanza-number-interface</keyword>
	<keyword>self-alignment-interface</keyword>
	<keyword>Span_arpeggio_engraver</keyword>
	<keyword>system-interface</keyword>
	<keyword>Engraver</keyword>
	<keyword>RhythmicStaff</keyword>
	<keyword>font-interface</keyword>
	<keyword>fret-diagram-interface</keyword>
	<keyword>Grace_spacing_engraver</keyword>
	<keyword>Bar_engraver</keyword>
	<keyword>unbreakable-spanner-interface</keyword>
	<keyword>Dynamic_engraver</keyword>
	<keyword>Grob_pq_engraver</keyword>
	<keyword>Default_bar_line_engraver</keyword>
	<keyword>Swallow_performer</keyword>
	<keyword>script-column-interface</keyword>
	<keyword>Piano_pedal_performer</keyword>
	<keyword>metronome-mark-interface</keyword>
	<keyword>melody-spanner-interface</keyword>
	<keyword>FretBoards</keyword>
	<keyword>spacing-spanner-interface</keyword>
	<keyword>Control_track_performer</keyword>
	<keyword>Break_align_engraver</keyword>
	<keyword>paper-column-interface</keyword>
	<keyword>PianoStaff</keyword>
	<keyword>Breathing_sign_engraver</keyword>
	<keyword>accidental-placement-interface</keyword>
	<keyword>Tuplet_engraver</keyword>
	<keyword>stroke-finger-interface</keyword>
	<keyword>side-position-interface</keyword>
	<keyword>note-name-interface</keyword>
	<keyword>bar-line-interface</keyword>
	<keyword>lyric-extender-interface</keyword>
	<keyword>Staff</keyword>
	<keyword>GregorianTranscriptionStaff</keyword>
	<keyword>Rest_swallow_translator</keyword>
	<keyword>dynamic-text-spanner-interface</keyword>
	<keyword>arpeggio-interface</keyword>
	<keyword>Cluster_spanner_engraver</keyword>
	<keyword>Collision_engraver</keyword>
	<keyword>accidental-interface</keyword>
	<keyword>rest-interface</keyword>
	<keyword>Tab_note_heads_engraver</keyword>
	<keyword>dots-interface</keyword>
	<keyword>staff-symbol-referencer-interface</keyword>
	<keyword>ambitus-interface</keyword>
	<keyword>bass-figure-interface</keyword>
	<keyword>vaticana-ligature-interface</keyword>
	<keyword>ledgered-interface</keyword>
	<keyword>item-interface</keyword>
	<keyword>Tie_performer</keyword>
	<keyword>volta-bracket-interface</keyword>
	<keyword>vertically-spaceable-interface</keyword>
	<keyword>Chord_tremolo_engraver</keyword>
	<keyword>note-column-interface</keyword>
	<keyword>DrumVoice</keyword>
	<keyword>axis-group-interface</keyword>
	<keyword>Ledger_line_engraver</keyword>
	<keyword>Slash_repeat_engraver</keyword>
	<keyword>ligature-bracket-interface</keyword>
	<keyword>Pitch_squash_engraver</keyword>
	<keyword>Instrument_switch_engraver</keyword>
	<keyword>Voice</keyword>
	<keyword>Script_column_engraver</keyword>
	<keyword>Volta_engraver</keyword>
	<keyword>Stanza_number_align_engraver</keyword>
	<keyword>Vertical_align_engraver</keyword>
	<keyword>span-bar-interface</keyword>
	<keyword>Staff_collecting_engraver</keyword>
	<keyword>Ligature_bracket_engraver</keyword>
	<keyword>Time_signature_engraver</keyword>
	<keyword>Beam_engraver</keyword>
	<keyword>Note_name_engraver</keyword>
	<keyword>Note_heads_engraver</keyword>
	<keyword>Forbid_line_break_engraver</keyword>
	<keyword>spacing-options-interface</keyword>
	<keyword>spacing-interface</keyword>
	<keyword>piano-pedal-script-interface</keyword>
	<keyword>MensuralStaff</keyword>
	<keyword>Global</keyword>
	<keyword>trill-pitch-accidental-interface</keyword>
	<keyword>grob-interface</keyword>
	<keyword>Horizontal_bracket_engraver</keyword>
	<keyword>Grid_line_span_engraver</keyword>
	<keyword>NoteNames</keyword>
	<keyword>piano-pedal-interface</keyword>
	<keyword>Axis_group_engraver</keyword>
	<keyword>Staff_symbol_engraver</keyword>
	<keyword>stem-interface</keyword>
	<keyword>Note_spacing_engraver</keyword>
	<keyword>Slur_engraver</keyword>
	<keyword>pitched-trill-interface</keyword>
	<keyword>tie-column-interface</keyword>
	<keyword>stem-tremolo-interface</keyword>
	<keyword>Grid_point_engraver</keyword>
	<keyword>System_start_delimiter_engraver</keyword>
	<keyword>Completion_heads_engraver</keyword>
	<keyword>Drum_notes_engraver</keyword>
	<keyword>Swallow_engraver</keyword>
	<keyword>Slur_performer</keyword>
	<keyword>ledger-line-spanner-interface</keyword>
	<keyword>key-cancellation-interface</keyword>
	<keyword>lyric-hyphen-interface</keyword>
	<keyword>Clef_engraver</keyword>
	<keyword>dynamic-interface</keyword>
	<keyword>Score</keyword>
	<keyword>Output_property_engraver</keyword>
	<keyword>Repeat_tie_engraver</keyword>
	<keyword>Rest_engraver</keyword>
	<keyword>break-aligned-interface</keyword>
	<keyword>String_number_engraver</keyword>
	<keyword>only-prebreak-interface</keyword>
	<keyword>Lyric_engraver</keyword>
	<keyword>Tempo_performer</keyword>
	<keyword>Parenthesis_engraver</keyword>
	<keyword>Repeat_acknowledge_engraver</keyword>
	<keyword>mensural-ligature-interface</keyword>
	<keyword>align-interface</keyword>
	<keyword>Stanza_number_engraver</keyword>
	<keyword>system-start-delimiter-interface</keyword>
	<keyword>lyric-syllable-interface</keyword>
	<keyword>bend-after-interface</keyword>
	<keyword>dynamic-line-spanner-interface</keyword>
	<keyword>Staff_performer</keyword>
	<keyword>Bar_number_engraver</keyword>
	<keyword>Fretboard_engraver</keyword>
	<keyword>tablature-interface</keyword>
	<keyword>Fingering_engraver</keyword>
	<keyword>chord-name-interface</keyword>
	<keyword>Note_swallow_translator</keyword>
	<keyword>Chord_name_engraver</keyword>
	<keyword>note-head-interface</keyword>
	<keyword>breathing-sign-interface</keyword>
	<keyword>Extender_engraver</keyword>
	<keyword>Ambitus_engraver</keyword>
	<keyword>DrumStaff</keyword>
	<keyword>dot-column-interface</keyword>
	<keyword>Lyric_performer</keyword>
	<keyword>enclosing-bracket-interface</keyword>
	<keyword>Trill_spanner_engraver</keyword>
	<keyword>Key_performer</keyword>
	<keyword>hairpin-interface</keyword>
	<keyword>Vertically_spaced_contexts_engraver</keyword>
	<keyword>Hyphen_engraver</keyword>
	<keyword>Dots_engraver</keyword>
	<keyword>multi-measure-rest-interface</keyword>
	<keyword>Multi_measure_rest_engraver</keyword>
	<keyword>Grace_beam_engraver</keyword>
	<keyword>separation-item-interface</keyword>
	<keyword>instrument-specific-markup-interface</keyword>
	<keyword>Balloon_engraver</keyword>
	<keyword>Translator</keyword>
	<keyword>Tweak_engraver</keyword>
	<keyword>Devnull</keyword>
	<keyword>Spacing_engraver</keyword>
	<keyword>Piano_pedal_align_engraver</keyword>
	<keyword>system-start-text-interface</keyword>
	<keyword>parentheses-interface</keyword>
	<keyword>ChoirStaff</keyword>
	<keyword>Span_bar_engraver</keyword>
	<keyword>Text_engraver</keyword>
	<keyword>GregorianTranscriptionVoice</keyword>
	<keyword>Timing_translator</keyword>
	<keyword>script-interface</keyword>
	<keyword>semi-tie-interface</keyword>
	<keyword>Percent_repeat_engraver</keyword>
	<keyword>break-alignable-interface</keyword>
	<keyword>Tab_staff_symbol_engraver</keyword>
	<keyword>line-interface</keyword>
	<keyword>rhythmic-grob-interface</keyword>
	<keyword>Dynamic_performer</keyword>
	<keyword>note-spacing-interface</keyword>
	<keyword>spanner-interface</keyword>
	<keyword>break-alignment-interface</keyword>
	<keyword>tuplet-number-interface</keyword>
	<keyword>Rhythmic_column_engraver</keyword>
	<keyword>cluster-beacon-interface</keyword>
	<keyword>horizontal-bracket-interface</keyword>
	<keyword>Mensural_ligature_engraver</keyword>
	<keyword>ChordNames</keyword>
	<keyword>gregorian-ligature-interface</keyword>
	<keyword>Melody_engraver</keyword>
	<keyword>ligature-interface</keyword>
	<keyword>Paper_column_engraver</keyword>
	<keyword>FiguredBass</keyword>
	<keyword>grace-spacing-interface</keyword>
	<keyword>tie-interface</keyword>
	<keyword>New_fingering_engraver</keyword>
	<keyword>Script_engraver</keyword>
	<keyword>Metronome_mark_engraver</keyword>
	<keyword>Tab_harmonic_engraver</keyword>
	<keyword>hara-kiri-group-spanner-interface</keyword>
	<keyword>string-number-interface</keyword>
	<keyword>Hara_kiri_engraver</keyword>
	<keyword>grid-line-interface</keyword>
	<keyword>Skip_event_swallow_translator</keyword>
	<keyword>Auto_beam_engraver</keyword>
	<keyword>balloon-interface</keyword>
	<keyword>spaceable-grob-interface</keyword>
	<keyword>trill-spanner-interface</keyword>
	<keyword>Font_size_engraver</keyword>
	<keyword>figured-bass-continuation-interface</keyword>
	<keyword>semi-tie-column-interface</keyword>
	<keyword>CueVoice</keyword>
	<keyword>Phrasing_slur_engraver</keyword>
	<keyword>Arpeggio_engraver</keyword>
	<keyword>mark-interface</keyword>
	<keyword>VaticanaStaff</keyword>
	<keyword>piano-pedal-bracket-interface</keyword>
	<keyword>beam-interface</keyword>
	<keyword>Note_performer</keyword>
	<keyword>custos-interface</keyword>
	<keyword>percent-repeat-interface</keyword>
	<keyword>time-signature-interface</keyword>
	<keyword>Custos_engraver</keyword>
	<keyword>Part_combine_engraver</keyword>
	<keyword>Piano_pedal_engraver</keyword>
	<keyword>tuplet-bracket-interface</keyword>
	<keyword>Stem_engraver</keyword>
	<keyword>finger-interface</keyword>
	<keyword>note-collision-interface</keyword>
	<keyword>Spanner_break_forbid_engraver</keyword>
	<keyword>Text_spanner_engraver</keyword>
	<keyword>Tie_engraver</keyword>
	<keyword>Figured_bass_position_engraver</keyword>
   </context>

    <context id="ly">
      <include>
        <context ref="line-comment"/>
        <context ref="comment"/>
      </include>
    </context>

  </definitions>
</language>
```

But, it still doesn't work :(. What am I doing wrong?

---

### Post by whannah on 2011-01-04
I just figured out how to get the warnings to go away!!! My office mate and I have been working on a scheme for NCAR's NCL language, but we've wasted horus trying to figure out how to get those pesky warnings for our custom styles like "ncl:comment".

So here's the deal, The "mapto" part of the "style" tag in the .lang file ONLY needs to be there when you are redirecting the style to something other than what it is set to be default. The default is always "language_id:style_id". In other words, if we have a language xyz and we want a new comment style, in the .lang file we would have this:

<style id="comment"  _name="Comment"/>

because when gedit loads this file, it will assume that the style is mapped to 

xyz:comment

which might be defined in classic.xml as

<style name="xyz:comment"  foreground="#708090" italic="true"/>

and if we were to put this instead:

<style id="comment"  _name="Comment"  mapto="xyz:comment"/>

Then gedit is trying to redirect this style back to itself which causes the warning.

Ta Da!


Hope this helps someone. If i had found a post like this it would have saved a good deal of time.

---

