# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

# AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

# APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

# LOGIC DIAGRAM

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
# PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

# VERILOG CODE
# ENCODER 
module enc8to3(e0,e1,e2,e3,e4,e5,e6,e7,d0,d1,d2);
input e0,e1,e2,e3,e4,e5,e6,e7;
output d0,d1,d2;
or g1(d0,e1,e3,e5,e7);
or g2(d1,e2,e3,e6,e7);
or g3(d2,e4,e5,e6,e7);
endmodule
# DECODER
module dec3to8(in_data,out_select);
input [7:0] in_data;
output reg [2:0] out_select;
always @* begin
  case (in_data)
    8'b00000001: out_select = 3'b000; 
    8'b00000010: out_select = 3'b001; 
    8'b00000100: out_select = 3'b010; 
    8'b00001000: out_select = 3'b011; 
    8'b00010000: out_select = 3'b100; 
    8'b00100000: out_select = 3'b101; 
    8'b01000000: out_select = 3'b110; 
    8'b10000000: out_select = 3'b111; 
    default: out_select = 3'b000; 
  endcase
end
endmodule
# MULTIPLEXER
module mux8t01(a,s,y);
input [7:0]a;
input [2:0]s;
output y;
reg y;
always@({s ,a})
  begin
    case(s)
     3'b000: y=a[0];
     3'b001: y=a[1];
     3'b010: y=a[2];
     3'b011: y=a[3];
     3'b100: y=a[4];
     3'b101: y=a[5];
     3'b110: y=a[6];
     3'b111: y=a[7];
   endcase
  end
endmodule
# DEMULTIPLEXER
module demux1t08(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s[2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
# MAGNITUDE COMPARATER
module magcomp(a, b, a_eq_b, a_lt_b,a_gt_b);
  input [3:0] a, b;
  output a_eq_b,a_lt_b,a_gt_b;
assign a_lt_b=(a<b);
assign a_gt_b=(a>b);
assign a_eq_b=(a==b);
endmodule
   
# OUTPUT WAVEFORM
# ENCODER
![image](https://github.com/sujitha18b/VLSI-LAB-EXP-2/assets/161813783/f1739ed9-0b4b-429e-8f2b-6fcfd6dc9069)
# DECODER
![image](https://github.com/sujitha18b/VLSI-LAB-EXP-2/assets/161813783/079045b9-e672-44d8-8e7b-cd625a885ce6)
# MULTIPLEXER
![image](https://github.com/sujitha18b/VLSI-LAB-EXP-2/assets/161813783/080abe62-11f7-47e1-86b9-478bbdbb1a78)
# DEMULTIPLEXER
![image](https://github.com/sujitha18b/VLSI-LAB-EXP-2/assets/161813783/f6432cc9-6d15-4b0e-bca7-43337c4d6eab)
# MAGNITUDE COMPARATER
![image](https://github.com/sujitha18b/VLSI-LAB-EXP-2/assets/161813783/437ae012-ef42-44be-aa96-907f1a662592)




# RESULT:
Thus the simulation and implementation of combinational logic circuit is done and outputs are verified successfully.


