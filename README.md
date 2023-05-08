Download Link: https://assignmentchef.com/product/solved-ve270-assignment-2-ssd-driver
<br>
To design a Seven-Segment Display (SSD) driver using Xilinx ISE, and to implement the circuit in an FPGA chip.

2. Background

An SSD consists of seven Light-Emitting Diodes (LEDs). Figure 1 shows the symbol of a single LED. Each LED has one anode (positive terminal) and one cathode (negative terminal). By applying higher level voltage on the anode and lower level voltage on the cathode, current will flow through the diode. When the voltage difference between the anode and cathode is big enough, the current will cause the LED to emit light. Seven LEDs are arranged in an SSD so that the lit LEDs can display a character. Figure 2 shows the structure of an SSD. The seven LEDs of a display are labeled as <strong>a</strong> through <strong>g</strong> by convention.

<strong>Figure 2. Seven-Segment Display </strong>

In an SSD, each LED can be turned on independently. By turning on carefully selected segments, different digits or characters may be displayed. For example, if segments <strong>a</strong>, <strong>b</strong>, <strong>c</strong>, <strong>d</strong>, and <strong>g</strong> are turned on and the remaining

segments are turned off, the SSD will display a  which is a “3”. Similarly, turning on <strong>a, b, c, e, f</strong>, and <strong>g</strong> will display a capital letter “A”.

In order to reduce the number of connections needed to turn on/off each of the segments, either the anodes or cathodes of the seven segments are tied together. The display will then be called <em>common anode</em> or <em>common cathode</em> SSD. In this lab we will design a driver for common anode SSD. The connection of a common anode SSD is shown in Figure 3. In the figure, the anodes of every LED is labeled commonly as <strong>A</strong>, while the cathodes are labeled as <strong>CA</strong> through <strong>CG</strong> for segments <strong>a</strong> to <strong>g</strong>, respectively. This labeling scheme is used in Figure 2 as well.

<strong>Figure 3. Connectivity of Common Anode SSD </strong>

3. Design Specification

An electronic driver is a circuit that provides signals to another device. SSD driver provides signals to the anodes and cathodes of an SSD to display a digit or alphabetic character. In this lab, you will be designing an SSD driver that takes a BCD number (4-bit binary number from 0000 to 1001) as input, and provides signals to the anodes and cathodes of an SSD to display the corresponding decimal digit.

The illumination of a common anode seven-segment display is primarily controlled by the common anode and secondarily by the seven cathodes. The anode of an SSD should receive a “1” for displaying. Nothing will be displayed if the anode is connected to “0”. To turn ON an LED of an SSD, a “0” must be provided to its cathode. As an example, to show the decimal number “3” on an SSD, the driver will receive “0011” as the inputs and will generate seven outputs “0000110” for the seven cathodes. The seven bits correspond to the cathodes of segments <strong>a, b, c, d, e, f</strong>, and <strong>g</strong>, respectively.

The Basys 3 board contains a four-digit common anode SSD. The anodes of the seven LEDs forming each digit are tied together into one “common anode” circuit node, but the LED cathodes remain separate. The common anode signals are available as four “digit enable” input signals to the 4-digit display. The cathodes of similar segments on all four displays are connected into seven circuit nodes labeled CA through CG (so, for example, the four <strong>d</strong> cathodes from the four digits are grouped together into a single circuit node called “CD”). These seven cathode signals are available as inputs to the 4-digit display. This signal connection scheme makes the cathode signals common to all digits but they can only illuminate the segments of a digit whose corresponding anode signal is asserted.

<strong>Figure 4. SSDs and their connections on Nexys2 FPGA board (Copied from Digilent Inc) </strong>

Figure 5 shows the block diagram of the design. The SSD Driver is the circuit you will be drawing using the software tool, and the other parts are hardware on the FPGA board. As shown in the figure, the circuit SSD Driver has four inputs, B3, B2, B1, and B0, which take the 4-bit binary number, assuming the inputs from 1010 to 1111 will never happen. It provides seven outputs CA, CB, CC, CD, CE, CF, and CG which are connected to the seven cathodes of the SSD. Four more output AN0 ~ AN3 are also given from the SSD Driver, which are used to enable one of the four SSDs and disable the rest.




<strong>NOTE: in Figure 5, the outputs AN0 ~ AN3 are connected to the common anodes through inverter-like parts. This connection is specific to the hardware platform that we are using.  </strong>







<strong>Figure 5. Block Diagram of Seven-Segment Display Driver </strong>




<h2>4. Drawing Schematics, simulate and implement the circuit</h2>




Draw the circuitry for the SSD driver using Multisim schematic capture tool. It’s highly suggested to create a hierarchical block or sub-circuit for each output equation. Make sure the inputs are labeled correctly.




Simulate the top-level integrated circuit using Multisim. Implement your design on the Basys 3 FPGA board.