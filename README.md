# differential-amp-
Basic operations on differential amplifier.


What is a Differential Amplifier??

   a Differential Amplifier is a type of amplifier which amplifies the dfference between two input  voltages and eleminates any common voltages that lies between the inputs. It has two inputs and one common output.This is why the differential amplifier is also known as a difference amplifier – the difference between the input voltages is amplified.

   The MOS differential pair is an amplifier configuration consisting of two identical, perfectly matched MOSFETs with equal source resistances and shared or matching inputs. The output voltage is determined by the difference between the drain voltages (V_D) of the two MOSFETs.

Differential amplifiers amplify the difference between two input signals rather than a single input, offering several advantages:

1.	They are more efficient compared to single MOSFET amplifiers.
 
2.	Due to their cancellation properties, they reject unwanted noise, known as common-mode noise, from the circuit.
 
3.	They inherently suppress interference that appears in both input signals, improving signal integrity.
 
4.	Common-mode signals, such as DC offsets present in both inputs, are rejected, allowing the amplifier to focus only on the desired signal. This is especially useful in IC design, as it eliminates the need for bulky DC-blocking capacitors.
 
5.	The subtraction performed by the differential pair makes it ideal for integration into negative-feedback amplifiers, significantly enhancing performance.


While these advantages might seem to come with major drawbacks, IC fabrication largely mitigates them. The higher component count is not a concern in IC design due to the minimal cost of adding transistors. Additionally, the requirement for matched components is effectively addressed through modern fabrication techniques, ensuring consistent component characteristics.

While a differential pair can also be constructed using BJTs, this experiment focuses specifically on MOSFETs. Since the differential amplifier (diff-amp) serves as the fundamental building block of an operational amplifier (op-amp), understanding its operation is crucial for gaining deeper insight into op-amps.

In practical applications, the current-source symbol would typically represent a circuit that generates a constant current. (For more details, refer to The Basic MOSFET Constant-Current Source.) However, to simplify our introductory analysis, we will use an ideal current source in our simulations instead of a practical constant-current circuit.

In an actual IC implementation, resistors would be replaced by a current mirror, which functions as an “active load.” However, to clearly understand the fundamental operation of the differential pair, we will first examine the resistor-based version.

For optimal performance, the differential pair relies on balance. This means the MOSFETs and resistors must be properly matched—both transistors should have identical channel dimensions, and the resistors should be equal, ensuring that R1 is the same as R2. The chosen resistance value for these resistors is referred to as R_D. 

  ![image](https://github.com/user-attachments/assets/3f7301d6-edda-4747-ab61-d38530ffa038)

EXPERIMENT 3:

Design and analyse differential amplifier with specifications given as follows : Vdd= 2.2V, P<=2.2mW, Vocm= 1.25V, Vicm= 1.2V, Vp=0.4V. Perform: DC analysis, transient analysis,frequency response and extract the parameters. length=180nm

![WhatsApp Image 2025-03-01 at 11 48 34_3cc1e488](https://github.com/user-attachments/assets/60287ca4-cb2d-478d-876e-06e86227b165)

Id>= P/Vdd (because P<= 2.2mA)
   = 2.2mV/2.2V
   =1mA


>Id1=(Id/2)

   =(1mA/2)

   =0.5mA


>Id2=Id-Id1
   
   =1mA-0.5mA
   
   =0.5mA

>Rd=(Vdd-Vocm)/Id1
  
   =(2.2-1.25)V/0.5mA
  
   =1.9k ohm


>Rss=(Vp/Iss)
  
   =0.4V/1mA
 
   =0.4k ohm
   
   =400 ohm

  DC Analysis:

  DC analysis examines a circuit’s behavior when a direct current (constant voltage) is applied. It helps determine key values such as current and voltage under steady-state conditions, where the circuit remains stable over time. This analysis reveals the operating points of transistors, including node voltages and current flow. Proper biasing is essential to ensure the amplifier functions in the correct region (saturation for MOSFETs), delivering the expected gain and performance.

Procedure for Performing DC Analysis:
 1.	Set appropriate values for the MOSFET’s length and width to ensure the desired current flows through each branch. For optimal operation, use a length of 180 nm and a width of 6.41246 μm.



![image](https://github.com/user-attachments/assets/66c1f09c-cb8c-4ec4-9f94-167aeb46225f)


 2.	Choose the DC operating point (DC op pnt) in the Edit Simulation Command and run the simulation. The figure below displays the values obtained from the DC analysis.From the figure above, we observe that the obtained current (I_DD) is 0.5 mA, which aligns with the design specifications for V_OCM and V_P. To verify this, we calculate the power using the formula P = V × I, ensuring that P ≤ 2.2 × 1m = 2.2 mW. This confirms that the power rating meets the requirement of 2.2 mW or lower.


  ![DC](https://github.com/user-attachments/assets/3266727d-d56e-442b-8684-b8b5f41d53d9)



  Transient Analysis:

  Transient analysis examines how the circuit responds to time-varying input signals. It allows us to observe key aspects of the amplifier’s performance, such as signal amplification, settling time, and transient distortions. This analysis is essential for evaluating how the circuit handles real-world signals and ensuring it produces the expected output without delays or unwanted oscillations.

  Procedure for Performing Transient Analysis:

  
1.	To conduct transient analysis, apply a sine wave input with an offset voltage of 1.2V, an amplitude of 50mV, and a frequency of 1 kHz to both gate voltage sources, then observe the circuit’s response.


 ![WhatsApp Image 2025-03-06 at 20 02 24_d14e639b](https://github.com/user-attachments/assets/2fa38552-0382-468b-9f3a-3460564abd2b)


 2.	Select Transient Analysis in the Edit Simulation Command, set the stop time to 5 ms, and run the simulation. Observe the graph of V_OCM (output) versus the input gate voltage to analyze the circuit’s behavior.


  ![transient](https://github.com/user-attachments/assets/d2bfa751-4377-43c4-abfa-ca6cfc10b880)



  AC Analysis:
  
  AC analysis evaluates the circuit’s frequency response, showing how gain, phase shift, and bandwidth vary with different input frequencies. This helps assess the amplifier’s real-world performance, ensuring stable gain and proper operation within the desired frequency range. AC analysis is also used to verify the gain obtained from transient analysis. In this process, the same sinusoidal signal is applied to the gate terminals, with the small-signal AC analysis amplitude set to 1, before running the simulation.


  ![ac](https://github.com/user-attachments/assets/d1aad008-1bf5-46f0-9c02-85fc9327a570)

Circuit 2

Resistor R_SS is replaced with a 1 mA current source to analyze the circuit.In a MOS differential amplifier, replacing the resistor with a current source enhances both gain and performance. A current source provides high output resistance, which increases the amplifier’s gain. It also ensures a stable and constant current flow, making the circuit more efficient and less sensitive to variations in power supply or transistor parameters. Additionally, a current source improves common-mode signal rejection, enhancing the amplifier’s differential performance. By maintaining a steady current, it reduces distortion and improves overall signal quality.

![2](https://github.com/user-attachments/assets/6c1bffa5-22fa-42f1-b692-5dafd5bb8f75)


DC Analysis:

![dc r](https://github.com/user-attachments/assets/c7dc9575-9f32-4a33-b8a6-d6847ba44e0f)


there is no much changes observed when we replace resistor by current source,only thing that gets enhanced is stability of the Vp.


Transien Analysis :

![transient 2](https://github.com/user-attachments/assets/66eb82ad-bb7b-4f4c-80ae-f0f1375d4487)

DC offset=1.2V

Amplitude=50m

Frequency= 1khz

We can see 180 degeree phse shift can be seen with respect to input. The gain is Vout by Vin which is nearly equal to 4(Av). Finally dB=20log(Av) = 12dB approximatly.


AC Analysis :

![ac 2](https://github.com/user-attachments/assets/6ab38786-966d-497b-bc34-2d8412135f3d)


n this setup, the same sinusoidal signal is applied to the gate terminals with a small-signal AC analysis amplitude of 1, followed by simulation. Comparing the results with the previous circuit that included resistor R_SS, we observe that the gain remains nearly unchanged, with only a negligible variation.

Circuit 3

In this setup, we replace resistor R_SS with an N-channel MOSFET to analyze the circuit’s behavior. In a MOS differential amplifier, swapping the resistor for a MOSFET acting as a current source helps improve performance. The MOSFET provides high output resistance, which boosts gain, while also maintaining a stable and constant current, ensuring better biasing and making the circuit less sensitive to power supply variations. Additionally, using a MOSFET instead of a resistor saves space in IC design and enhances common-mode signal rejection, making the amplifier more efficient. This experiment demonstrates how the MOSFET effectively functions as a constant current source.







  



  


  



  


   


