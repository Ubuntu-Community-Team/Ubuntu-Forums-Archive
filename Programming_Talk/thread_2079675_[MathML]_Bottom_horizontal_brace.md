---
title: "[MathML] Bottom horizontal brace"
date: 2012-11-02
forum: Programming Talk
---

### Post by bird1500 on 2012-11-02
Hi,
How can I draw the bottom horizontal brace from the screenshot?

So far I could only implement the bottom equation itself, without the brace:
[PHP]
<math xmlns="http://www.w3.org/1998/Math/MathML">
<mo>=</mo>
<mfrac bevelled="true">
    <mrow>
        <mo>(</mo>
        <mfrac>
            <mrow><mn>2</mn><mi>n</mi></mrow>
            <mrow><mi>r</mi><mo>-</mo><mi>l</mi></mrow>
        </mfrac>
        <mo>&#x22C5;</mo>
        <msub><mi>x</mi><mi>e</mi></msub>
        <mo>+</mo>
        <mfrac>
            <mrow><mi>r</mi><mo>+</mo><mi>l</mi></mrow>
            <mrow><mi>r</mi><mo>-</mo><mi>l</mi></mrow>
        </mfrac>
        <mo>&#x22C5;</mo>
        <msub><mi>z</mi><mi>e</mi></msub>
        <mo>)</mo>
    </mrow>
    <msub><mi>&minus;z</mi><mi>e</mi></msub>
</mfrac>

</math>
[/PHP]

---

### Post by spjackson on 2012-11-02
[This]("https://developer.mozilla.org/en-US/docs/Mozilla_MathML_Project/MathML_Torture_Test") has an example in row 22 of the table.

---

### Post by bird1500 on 2012-11-02
Thanks buddy, it works, the tag "munder" is the key.

---

