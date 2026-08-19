# FF_blocking_non-blocking
# EXPERIMENT 3A: Simulation of All Flip-Flops using Blocking Statement
# AIM
To design and simulate basic flip-flops (SR, D, JK, and T) using blocking statements in Verilog HDL, and verify their functionality through simulation in Vivado 2023.1.

# APPARATUS REQUIRED
Vivado 2023.1
Computer with HDL Simulator
# DESCRIPTION
Flip-flops are the basic memory elements in sequential circuits.
In this experiment, different types of flip-flops (SR, D, JK, T) are modeled using behavioral modeling with blocking assignment (=) inside the always block.
Blocking assignments execute sequentially in the given order, which makes it easier to describe simple synchronous circuits.

# PROCEDURE
Open Vivado 2023.1.
Create a New RTL Project (e.g., FlipFlop_Simulation).
Add Verilog source files for each flip-flop (SR, D, JK, T).
Add a testbench file to verify all flip-flops.
Run Behavioral Simulation.
Observe waveforms of inputs and outputs for each flip-flop.
Verify that outputs match the truth table.
Save results and capture simulation screenshots.
# VERILOG CODE
**SR Flip-Flop (Non Blocking)**
```
module sr_ff (
    input wire S, R, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
**SR Flip-Flop Test bench**

module tb_sr_flipflop;

    reg S, R, clk;
    wire Q, Qbar;

    // Instantiate DUT
    sr_flipflop uut (
        .S(S),
        .R(R),
        .clk(clk),
        .Q(Q),
        .Qbar(Qbar)
    );

    // Clock generation
    always #5 clk = ~clk;

    initial begin

        clk = 0;
        S = 0;
        R = 0;

        $monitor("Time=%0t | S=%b R=%b CLK=%b | Q=%b Qbar=%b",
                  $time, S, R, clk, Q, Qbar);

        // No change
        #10 S = 0; R = 0;

        // Set
        #10 S = 1; R = 0;

        // Hold
        #10 S = 0; R = 0;

        // Reset
        #10 S = 0; R = 1;

        // Hold
        #10 S = 0; R = 0;

        // Invalid condition
        #10 S = 1; R = 1;

        #10 $finish;
    end

endmodule

**SIMULATION OUTPUT**

<img width="1633" height="907" alt="Screenshot 2026-08-19 114844" src="https://github.com/user-attachments/assets/00ff8d00-8472-4f12-9ac3-4c8e5f7bfeac" />

**JK Flip-Flop (Non Blocking)**
```
module jk_ff (
    input wire J, K, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
**JK Flip-Flop Test bench**
module tb_jk_flipflop;

    reg J, K, clk;
    wire Q, Qbar;

    jk_flipflop uut (
        .J(J),
        .K(K),
        .clk(clk),
        .Q(Q),
        .Qbar(Qbar)
    );

    always #5 clk = ~clk;

    initial begin
        clk = 0;
        J = 0;
        K = 0;

        #10 J = 0; K = 0;   // Hold
        #10 J = 1; K = 0;   // Set
        #10 J = 0; K = 0;   // Hold
        #10 J = 0; K = 1;   // Reset
        #10 J = 1; K = 1;   // Toggle
        #10 J = 1; K = 1;   // Toggle

        #10 $finish;
    end

    initial begin
        $monitor("Time=%0t J=%b K=%b CLK=%b Q=%b Qbar=%b",
                  $time, J, K, clk, Q, Qbar);
    end

endmodule

**SIMULATION OUTPUT**
<img width="1628" height="906" alt="Screenshot 2026-08-19 115426" src="https://github.com/user-attachments/assets/6dbff31c-acf1-49b2-ba5c-b8785d96c1a9" />


**D Flip-Flop (Non Blocking)**
```
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
**D Flip-Flop Test bench**

module tb_d_flipflop;

    reg D, clk;
    wire Q, Qbar;

    // Instantiate D Flip-Flop
    d_flipflop uut (
        .D(D),
        .clk(clk),
        .Q(Q),
        .Qbar(Qbar)
    );

    // Clock generation
    always #5 clk = ~clk;

    initial begin

        clk = 0;
        D = 0;

        $monitor("Time=%0t | D=%b CLK=%b | Q=%b Qbar=%b",
                  $time, D, clk, Q, Qbar);

        // D = 0
        #10 D = 0;

        // D = 1
        #10 D = 1;

        // D = 0
        #10 D = 0;

        // D = 1
        #10 D = 1;

        #10 $finish;
    end

endmodule

**SIMULATION OUTPUT**
<img width="1630" height="925" alt="Screenshot 2026-08-19 134057" src="https://github.com/user-attachments/assets/f8b422dc-2b11-48d6-9bc9-f54232067125" />


**T Flip-Flop (Non Blocking)**
```
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
**T Flip-Flop Test bench**

module tb_t_flipflop;

    reg T, clk;
    wire Q, Qbar;

    // Instantiate T Flip-Flop
    t_flipflop uut (
        .T(T),
        .clk(clk),
        .Q(Q),
        .Qbar(Qbar)
    );

    // Clock generation
    always #5 clk = ~clk;

    initial begin

        clk = 0;
        T = 0;

        $monitor("Time=%0t | T=%b CLK=%b | Q=%b Qbar=%b",
                  $time, T, clk, Q, Qbar);

        // T = 0 -> Hold
        #10 T = 0;

        // T = 1 -> Toggle
        #10 T = 1;

        // T = 1 -> Toggle
        #10 T = 1;

        // T = 0 -> Hold
        #10 T = 0;

        // T = 1 -> Toggle
        #10 T = 1;

        #10 $finish;
    end

endmodule

**SIMULATION OUTPUT**
<img width="1623" height="885" alt="Screenshot 2026-08-19 134711" src="https://github.com/user-attachments/assets/24301b67-6430-4679-acc1-aff71fd4249f" />


# RESULT
All flip-flops (SR, D, JK, T) were successfully simulated using Non blocking statements in Verilog HDL. The outputs matched the expected truth table values, demonstrating correct sequential behavior.
