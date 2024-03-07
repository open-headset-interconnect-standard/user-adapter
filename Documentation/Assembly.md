# 1. OHIS User Adapter

<style>
    h1    {background-color: #d4ebf2; border-bottom: 2px solid black; }
    h2    {background-color: #c1e1ec; border-bottom: 2px solid black; }
    h3    {background-color: #add8e6; border-bottom: 1px solid black; }
    h4    {background-color: #99cfe0; border-bottom: 1px solid black; }
    .note {background-color: #b0ffb0; }
    .warning {background-color: #ffffb0; }
</style>

Thank you for participating in the Open Headset Interconnect Standard (OHIS) ecosystem.  Whether you've sourced the parts yourself, or purchased a pre-made kit, you are helping the amateur radio community adopt an actual standard for the interface between the radio and the user.

<img src="Images/Glamour Oblique 3.5mm side.JPG" alt="OHIS User Adapter, Assembled" width=100%>

This is the OHIS User Adapter, an open source device that converts your headset whatever it is, to an OHIS standard interface.  With this adapter on your headset, you can connect your headset to any OHIS compliant radio or other device.

This is an Open Source (free as in speech) project.  The files and documentation can be found at: <https://github.com/open-headset-interconnect-standard/user-adapter>  Any/Everyone is encouraged to build these themselves if they desire.  In addition, some companies will sell these parts as a kit or preassembled device.

> <span class=note>**Note:**</span> This document will refer to OHIS User Adapter as "a kit" regardless of how you acquired the parts.

The authoritative location for this design and document is:  
<https://github.com/open-headset-interconnect-standard/user-adapter>

<div class="page" />

## 1.1. Document History

| Date | Version | Description |
|------|---------|-------------|
| 2024-02-27 | v0.1 | Starting work. |
| 2024-03-06 | v1.0 | First public release.<br/>Document v1.3 Mic level adjust jumper |

<div class="page" />

## 1.2. Table of Contents

- [1. OHIS User Adapter](#1-ohis-user-adapter)
    - [1.1. Document History](#11-document-history)
    - [1.2. Table of Contents](#12-table-of-contents)
- [2. What is OHIS](#2-what-is-ohis)
    - [2.1. Where does the OHIS User Adapter fit in all this](#21-where-does-the-ohis-user-adapter-fit-in-all-this)
- [3. Assembly](#3-assembly)
    - [3.1. Parts](#31-parts)
    - [3.2. Solder components](#32-solder-components)
        - [3.2.1. Resistors](#321-resistors)
        - [3.2.2. Transistor](#322-transistor)
        - [3.2.3. Capacitors](#323-capacitors)
        - [3.2.4. Configuration Headers](#324-configuration-headers)
        - [3.2.5. Connectors](#325-connectors)
        - [3.2.6. Button](#326-button)
        - [3.2.7. Version 1.3 And Later Kits Only](#327-version-13-and-later-kits-only)
    - [3.3. Mechanical Assembly](#33-mechanical-assembly)
        - [3.3.1. Identify the boards](#331-identify-the-boards)
            - [3.3.1.1. Bottom board](#3311-bottom-board)
            - [3.3.1.2. Top board](#3312-top-board)
        - [3.3.2. Assemble the stack](#332-assemble-the-stack)
            - [3.3.2.1. Screws](#3321-screws)
            - [3.3.2.2. Nylon spacers](#3322-nylon-spacers)
            - [3.3.2.3. Main board](#3323-main-board)
            - [3.3.2.4. Brass stand-offs](#3324-brass-stand-offs)
            - [3.3.2.5. Top board](#3325-top-board)
- [4. Configuration](#4-configuration)
    - [4.1. Electret or Dynamic](#41-electret-or-dynamic)
        - [4.1.1. Electret microphone](#411-electret-microphone)
        - [4.1.2. Dynamic microphone](#412-dynamic-microphone)
    - [4.2. Headphones or CTIA Headset](#42-headphones-or-ctia-headset)
        - [4.2.1. Headphones](#421-headphones)
        - [4.2.2. CTIA Headset](#422-ctia-headset)
    - [4.3. Adjusting Mic Level](#43-adjusting-mic-level)
        - [4.3.1. Activating the Mic Level circuit](#431-activating-the-mic-level-circuit)
        - [4.3.2. Adjusting the Mic Level](#432-adjusting-the-mic-level)
- [5. FAQ: Frequently Asked Questions](#5-faq-frequently-asked-questions)
    - [5.1. No microphone audio](#51-no-microphone-audio)

<div class="page" />

# 2. What is OHIS

The Open Headset Interconnect Standard is an open (free like speech) standard for the interface between the radio and the user.  Without OHIS, every radio manufacturer uses different connectors, different pinouts, and even different electrical standards for their microphone/audio inputs, speakers/audio outputs, and occasionally even PTT signal.  OHIS standardizes these into a single cable.

Full details cat be found at <https://ohis.org>, but here is a quick summary:

<img src="Images/OHIS Overview - User Adapter Highlighted.drawio.png" alt="An overview of an OHIS Ecosystem">

Ideally, headset and radios would support OHIS natively (top row).  Then any headset could connect directly to any radio without any adapters.

In the mean time, we need to use adapters that convert from whatever the headset or radio uses natively, to the OHIS standard.

But instead of needing one adapter that is unique to every pairing of headset and radio, by splitting the adapter in two with a standard interface in between them, any headset only ever needs one adapter, and any radio only ever needs one adapter.

The adapter on the headset side, called the **User adapter**, is unique to the headset (other microphone/speaker/PTT combo), and is irrespective of the radio it connects to.  Simiarly, the adapter on the radio side, called the **Radio adapter**, is unique to the radio (or other device that consumes a microphone and PTT, and generates a headphone/speaker), and is irrespective of the headset it connects to.

<div class="page" />

## 2.1. Where does the OHIS User Adapter fit in all this

This kit is a **User adapter** (as described above).  It is an open source (free like speech) project that anyone can create/build/modify/use in their own product, subject to the [Creative Commons CC-BY license](https://creativecommons.org/licenses/by/4.0/).

> <span class=note>**tl,dr:**</span> The Creative Commons Attribution license (CC-BY) means you can use this for anything you want, including in commercial products, as long as you acknowledge that you got the design, or at least the start of the design, from the OHIS Working Group.

This kit is designed to work with the following hardware:

* Microphone: Either an Electret or Dynamic microphone.  For the more technically minded:
    * Electret: -42dBv ~ -48dBv into 600 to 1k ohm load.  DC bias voltage provided.
    * Dynamic: -60dBv ~ -50dBv into 600 to 1k ohm load.  No DC bias voltage.
    * I've heard tell that it will also work on modern aviation headsets, which are technically "Carbon Equivalent" mic elements, but most of them are actually Electrets under the hood.
* Headphone: Any typical headphones will work.  For the more technically minded:
    * Headphones: 0dBv ~ -10dBv at full volume into 16 ~ 64ohm.
    * Line Level: 0dBv ~ -10dBv at full volume into 600 to 1k ohm load.  (Headphones out work well into a Line Level load.)
* PTT: A simple contact closure to ground.
    * Read: a button.

<div class="page" />

# 3. Assembly

This kit is a good starting point for people new to soldering.  It's entirely through-hole, not tightly packed, and only one part is static sensitive (the transistor) and it's pretty darn resilient.

> <span class=warning>**Warning:**</span> If this *isn't* your first rodeo, if you're a kit building pro, you can probably assemble this kit just using the component values printed on the circuit board. If you have a v1.2 kit, **DO NOT INSTALL** (yet): RV1 (1k trim pot) or C2 (47uF Electrolytic capacitor).  You'll decide whether to install them in [section 4.3: Adjusting Mic Level](#43-adjusting-mic-level).

## 3.1. Parts

Make sure you have all the parts:

![Kit parts](Images/All%20Parts.JPG)

List of all parts:

| Quantity | Reference | Description |
|----------|-----------|-------------|
| 1 | | Main circuit board, with all the components and traces. |
| 1 | | Top panel circuit board, with a hole labeled "PTT". |
| 1 | | Bottom panel circuit board, no features other than the 4 screw holes that are also on all other boards. |
| 1 | J1 | RJ-45 socket |
| 3 | J2, J3, J4 | 3.5mm TRRS sockets |
| 1 | J5 | 2x2 or 2x3 right angle pin header (v1.2 uses 2x2, >= v1.3 uses 2x3) |
| 1 | J6 | 2x3 right angle pin header |
| 4 | | Jumpers |
| 1 | C1 | 1uF ceramic capacitor, labeled 105 (little blue circular thing, with wide spread leads) |
| 1 | C2 | 47uF electrolytic capacitor (looks like a small can) |
| 1 | C3 | 1nF ceramic capacitor, labeled 102 (little blue circular thing, with close spaced leads) |
| 1 | RV1 | 1k ohm trim pot |
| 1 | Q1 | 2N3904 transistor (or similar) |
| 1 | R1 | 75k ohm resistor: Purple - Green - Orange - Gold |
| 1 | R2 | 27k ohm resistor: Red - Purple - Orange - Gold |
| 1 | R3 | 470 ohm resistor: Yellow - Purple - Brown - Gold |
| 1 | SW1 | Button, 16mm tall |
| 1 | | Button cap, yellow |
| 4 | | M3 x 6mm philips head screw |
| 4 | | M3 x 10mm philips head screw |
| 4 | | M3 14mm brass hex stand-off |
| 4 | | M3 2mm nylon washer/spacer |

If you purchased this kit from someone and any of the parts are missing, contact them to get the missing parts.

<div class="page" />

## 3.2. Solder components

This document assumes you know how to solder reasonably well.  If you'd like a refresher, there are many good video tutorials on sites like YouTube.  This is a good written tutorial from SparkFun: <https://learn.sparkfun.com/tutorials/how-to-solder-through-hole-soldering>.

> <span class=note>**Note:**</span> The pictures that follow show brass stand-offs screwed into the holes of the main board.  This is only for staging the photographs, so the camera wasn't looking straight down on the board.  Don't do anything with the screws and stand-offs yet; they will get installed differently later.

Start by soldering the components to the main board, shortest/smallest components first.

### 3.2.1. Resistors

<img src="Images/How to install vertical resistors.JPG" alt="Resistor installation" width=80%>

The resistors are installed vertically.  Fold one lead down (doesn't matter which, polarity isn't important) nearly 180 degrees so it's next to, and mostly parallel with, the body of the resistor.  Insert the resistor such that the body is in the pad with the white silkscreen circle.

[ ] R1, 75k: Purple Green Orange Gold.  
[ ] R2, 27k: Red Purple Orange Gold.  
[ ] R3, 470: Yellow Purple Brown Gold.  

<img src="Images/Installed Resistors.JPG" alt="Resistor installation" width=80%>

<div class="page" />

### 3.2.2. Transistor

The transistor is squoze (yes that's a word) between the resistors, so lets do it next.

The transistor IS polarity sensitive.  Make sure the body of the transistor is inserted the same way its drawn on the board: the flat side of the transistor is on the left side, facing the 3.5mm sockets.

[ ] Q1, 3N3904  

<img src="Images/Installed Transistor.JPG" alt="Transistor installation" width=80%>

### 3.2.3. Capacitors

[ ] C1, 1uF Ceramic: Blue capacitor, marked "105", with wide spaced leads.  
[ ] C2, 47uF Electrolytic: **DO NOT INSTALL YET**  You'll determine whether it's necessary in [section 4.3](#43-adjusting-mic-level)  
[ ] C3, 1nF Ceramic: Blue capacitor, marked "102", with close spaced leads  

<img src="Images/Installed Capacitors.JPG" alt="Capacitor installation" width=80%>

<div class="page" />

### 3.2.4. Configuration Headers

Configuration headers are designed to be accessible from the side of the final device, hence the right-angle connectors.  Insert them in the orientation as drawn on the board.

I find its easiest to insert the header, then flip the board over holding the header in using one finger on only one end of the header.  Then solder just one pin in place (preferably not the pin you're holding with your finger).  Then you can adjust the orientation of the headers by re-heating only that one pin.  Once you're happy with the orientation, solder the rest of the pins.

[ ] J5, 2x2 right angle pin headers, or 2x3 right angle pin headers >= for v1.3  
[ ] J6, 2x3 right angle pin headers  

<img src="Images/Installed Headers.JPG" alt="Headers installation" width=80%>

### 3.2.5. Connectors

There is only one orientation that any of these connectors fit in the board.  All three of the 3.5mm sockets are the same; it doesn't matter which one is used where.

[ ] J1, RJ-45 socket, "OHIS"  
[ ] J2, 3.5mm socket, "Phones"  
[ ] J3, 3.5mm socket, "Mic"  
[ ] J4, 3.5mm socket, "PTT"  

<img src="Images/Installed Connectors.JPG" alt="Connectors installation" width=80%>

<div class="page" />

### 3.2.6. Button

The button is not polarity sensitive.  It can go in either orientation.  When soldering it down, make sure the button is parallel with the board (it might not be perfectly flush) so that the button's shaft is perpendicular to the board.  This button will stick through the top board, so it needs to be in the correct position.

[ ] SW1, 16mm tall push button  
[ ] Glue the cap on top of the button.  A small dab of CA glue (eg: SuperGlue), E6000, or simple white glue works.  

<img src="Images/Installed Button.JPG" alt="Button installation" width=80%>

### 3.2.7. Version 1.3 And Later Kits Only

If your board is a v1.3 or later, then install the following components as well.

[ ] C2, 47uF Electrolytic Capacitor.  
[ ] RV1, 1k trim pot.  

<img src="Images/Installed Trim Pot and C2.JPG" alt="Capacitor and trim pot installation" width=80%>

If your board is a v1.2, you will determine whether to install these parts in [section 4.3: Adjusting Mic Level](#43-adjusting-mic-level)

<div class="page" />

## 3.3. Mechanical Assembly

The main board you just assembled will be sandwiched between the other two boards, all of it held together in a stack with the screws and standoffs.  When you're done, it will look like this:

<img src="Images/Assembled Fully - Side View.JPG" alt="Fully assembled side view" width=80%>

### 3.3.1. Identify the boards

#### 3.3.1.1. Bottom board

The bottom board is the one *without* the hole labeled PTT:

<img src="Images/Board Bottom.JPG" alt="Bottom board" width=60%>

#### 3.3.1.2. Top board

The top board is the one *with* the hole labeled PTT.  It also has a large square of exposed metal on the bottom of the other end of the board:

<img src="Images/Board Top.JPG" alt="Top board" width=60%>

The bottom of the bottom board, and the top of the top board, are the sides with the silkscreen'd text and OHIS logos.  These sides will be on the outside of the stack.

<div class="page" />

### 3.3.2. Assemble the stack

Identify the parts you'll need:

<img src="Images/Assembled Bottom Board.JPG" alt="Identify the parts you need" width=60%>

* Bottom board  
* 4x M3 10mm philips head screws  
* 4x M3 Nylon spacers  
* Main board, what you just assembled  
* 4x M3 14mm brass stand-offs  
* Top board
* 4x M3 6mm philips head screws

<div class="page" />

#### 3.3.2.1. Screws

Start by inserting all four of the M3 x 10mm screws (the longer screws) in from the bottom of the bottom board. Place the bottom board on your work surface, so that the four screws are poking up, with the screw heads below:

[ ] Bottom board  
[ ] 4x M3 10mm philips head screws  

<img src="Images/Assembled Bottom Screws.JPG" alt="Screws inserted" width=60%>

#### 3.3.2.2. Nylon spacers

Slide the four nylon washers/spacers over the exposed screws:

[ ] 4x M3 Nylon spacers  

<img src="Images/Assembled Nylon Spacers.JPG" alt="Nylon spacers installed" width=60%>

<div class="page" />

#### 3.3.2.3. Main board

Slide the main board that you just assembled over the four screws, with the components facing up:

[ ] Main board  

<img src="Images/Assembled Main Board.JPG" alt="Main board installed" width=60%>

#### 3.3.2.4. Brass stand-offs

Screw the brass stand-offs on the exposed screws. Just get the stand-offs started on the screws so they won't fall out, then you can pick up the whole assembly and tighten the screws/stand-offs:

[ ] 4x M3 14mm brass stand-offs  

<img src="Images/Assembled Standoffs.JPG" alt="Brass standoffs installed" width=60%>

<div class="page" />

#### 3.3.2.5. Top board

Screw the top board to the top of the four stand-offs, using the four M3 x 6mm screws. Make sure you line up the whole in the top board labeled PTT with the PTT button on the main board:

<img src="Images/Assembled Top Board.JPG" alt="Top board installed" width=60%>

The stack-up should look like this when you're done:

<img src="Images/Assembled Fully - Side View.JPG" alt="Top board installed, side view." width=60%>

<div class="page" />

# 4. Configuration

## 4.1. Electret or Dynamic

The OHIS User Adapter kit will work with either an Electret or Dynamic mic elements.  You select which one to use by placing two jumpers on J5, the 2x2 right angle pin header to the "right" (when looking at the side of the assembled kit from the side with the exposed pins.)

> <span class=note>**Note:**</span> If your kit is v1.3 or later, it will be a 2x3 right angle pin header.  The instructions below still apply to the 2x2 pins on the left side of the jumper.  You'll configure the right most 2 pins in [section 4.3 below](#43-adjusting-mic-level).

### 4.1.1. Electret microphone

To select Electret, place the two jumpers horizontal, so that they are parallel with the board:

<img src="Images/Jumpers Electret.JPG" alt="Jumpers configured for Electret microphone" width=60%>

### 4.1.2. Dynamic microphone

To select Dynamic, place the two jumpers vertical, so that they are perpendicular with the board:

<img src="Images/Jumpers Dynamic.JPG" alt="Jumpers configured for Dynamic microphone" width=60%>

<div class="page" />

## 4.2. Headphones or CTIA Headset

The "Phones" connector can be configured for either normal headphones (3 pin TRS plugs for each headphones, and microphone), or for a CTIA headset (4 pin TRRS plug, with microphone on the one connector).

### 4.2.1. Headphones

To select normal 3-pin TRS headphones, place two jumpers parallel with the board, in the left most position: 

<img src="Images/Jumpers Phones.JPG" alt="Jumpers configured for regular headphones" width=60%>

Then insert the headphone connector (usually green) in the "Phones" socket, and the microphone connector (usually red) in the "Mic" socket.

### 4.2.2. CTIA Headset

To select CTIA 4-pin TRRS headset with integrated microphone, place two jumpers parallel with the board, in the right most position.

<img src="Images/Jumpers CTIA.JPG" alt="Jumpers configured for CTIA headsets" width=60%>

Then insert the CTIA plug in the "Phones" socket.  The "Mic" is unused.

<div class="page" />

## 4.3. Adjusting Mic Level

Your microphone will likely not need any adjustment.  The OHIS standard is "Electret Microphone Level."  Meaning, connecting an electret microphone directly to the OHIS connector should give you the correct mic level.  Similarly, the dynamic microphone pre-amp on the OHIS User Adapter is designed to give just about the right amount of gain to make a typical dynamic mic about as loud as a typical electret.

Having said that, all mics are a little different, and how users' hold their microphones can change how loud the mic is.

For v1.3 and later kits, remove the jumper from the right most 2 pins of the Mic Type header.  This removes the Mic level adjust circuit.  For v1.2 kits, you haven't yet installed the Mic level adjust circuit (RV1 and C2).

Then connect your OHIS User Adapter to: and OHIS Radio adapter, an OHIS level measuring device, etc.  Talk into the microphone as you would while operating the radio normally.  Notice whether you're over-driving the radio, or whether the level measuring device says your signal is too loud.  If it is too loud, proceed to Activating and Adjusting the Mic level.

### 4.3.1. Activating the Mic Level circuit

For v1.2 kits, install RV1 (1k trim pot) and C2 (47uF electrolytic capacitor), as in [section 3.2.7](#327-v13-and-later-kits-only).

For v1.3 kits, install a jumper on the right most two pins of the "Mic Type" headers.

### 4.3.2. Adjusting the Mic Level

Connect your OHIS User Adapter to the same system you used for measuring the microphone level before.  Then use a small screwdriver (either philips or slotted) to adjust the microphone level until it's correct.

> <span class=note>**Note:**</span> Just having the Mic level adjust circuit installed drops the microphone level a little bit, even when it is trimmed all the way "loud."  This is why you start with it deactivated earlier (v1.2: not installed, v1.3: jumper removed).  Only activate it if necessary.

<div class="page" />

# 5. FAQ: Frequently Asked Questions

## 5.1. No microphone audio

* Confirm the "Phones type" header jumpers.  If those jumpers are set wrong, the symptom will be "no microphone audio."
    * If using a headset with separate microphone and headphone connector, confirm:
        * The headphone plug is in the "Phones" socket.
        * The microphone plug is in the "Mic" socket.
        * The "Phones type" jumpers are in the "Phones" position, to the left.
    * If using a headset with a single 4 pin TRRS connector, confirm:
        * The headset plug is in the "Phones" socket.
        * The "Mic" socket is unused.
        * The "Phones type" jumpers are in the "CTIA" position, to the right.
        * The "Mic type" jumpers are in the "Electret" position, horizontal parallel to the circuit board.
* Confirm the "Mic type" header jumpers.  If those jumpers are set wrong, the symptom will *also* be "no microphone audio."
    * Examples of Electret microphones:
        * 4 pin TRRS CTIA headsets
        * "PC Gaming" headset
        * Mobile phone headset
        * RadioSport headsets
        * Heil headset with an "iC" microphone element for an Icom radio
    * Examples of Dynamic microphones:
        * Heil headset with any other microphone element (for Yaesu, Kenwood, etc)
            * Heil are Dynamic by default; you have to explicitly select the "iC" mic element if you're using it with an Icom radio.
        * A studio microphone with an XLR connector (using a 3.5mm TRS to XLR cable)

