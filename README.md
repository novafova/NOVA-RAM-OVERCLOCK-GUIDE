# NOVA-RAM-OVERCLOCK-GUIDE
A full RAM Overclocking Guide

Comprehensive RAM Overclocking Guide
DDR4 & DDR5 Memory Tuning, Timings, Voltages, Stability Testing, IC Types, and Performance Optimization
Table of Contents
Introduction
RAM Overclocking Basics
DDR4 vs DDR5 Differences
Memory Frequency Explained
Infinity Fabric / Gear Ratios
RAM Timings Explained
Primary Timings
Secondary Timings
Tertiary Timings
Voltages Explained
Memory IC (Die) Types
How to Identify Your RAM Die
AMD RAM Overclocking
Intel RAM Overclocking
BIOS Navigation Guide
Step-by-Step Overclocking Workflow
Stability Testing
Error Diagnosis
Safe Voltage Limits
Timing Tightening Strategy
Frequency Scaling Strategy
Command Rate & Gear Down Mode
PMIC Unlocking (DDR5)
Cooling & Thermal Management
Benchmarking
Example Configurations
Advanced Tuning
Troubleshooting
Common Myths
Recommended Tools
Glossary
Final Notes
1. Introduction

RAM overclocking improves:

FPS consistency
1% lows
latency
memory bandwidth
application responsiveness
compression/rendering performance

Unlike CPU overclocking, memory tuning heavily affects latency-sensitive games like:

Fortnite
Valorant
CS2
Rust
Tarkov

Memory tuning is one of the biggest hidden performance gains in modern systems.

2. RAM Overclocking Basics

RAM performance depends on:

Factor	What It Does
Frequency	Increases bandwidth
Timings	Reduces latency
Voltages	Stabilizes higher clocks
Memory Controller	CPU’s ability to handle memory
IC Quality	Determines scaling potential
3. DDR4 vs DDR5 Differences
Feature	DDR4	DDR5
Voltage Regulation	Motherboard	On-DIMM PMIC
Frequency Range	2133–5000+	4800–9000+
Latency	Lower absolute	Higher absolute
Bandwidth	Lower	Much higher
Gear Modes	Rare	Extremely important
Stability Complexity	Moderate	High
4. Memory Frequency Explained

RAM speed is measured in MT/s.

Examples:

DDR4-3200
DDR5-6000
DDR5-8000

Higher frequency:

increases bandwidth
can reduce performance if latency becomes too high

Memory latency formula:

Latency(ns)=
Frequency
CL×2000
	​


Example:

6000 CL30 = 10ns
6400 CL32 = 10ns

Not all higher frequencies are faster in real-world gaming.

5. Infinity Fabric / Gear Ratios
AMD

Important clocks:

Clock	Purpose
MCLK	Memory Clock
UCLK	Memory Controller
FCLK	Infinity Fabric

Optimal AMD setup:

1:1 ratio
UCLK = MCLK

Common sweet spots:

CPU	Sweet Spot
Ryzen 5000	DDR4 3600
Ryzen 7000	DDR5 6000
Ryzen 9000	DDR5 6200–6400
Intel

Intel uses:

Gear 1
Gear 2
Gear 4
Gear	Meaning
Gear 1	Controller synced
Gear 2	Controller half speed
Gear 4	Quarter speed

Gear 1 has lowest latency.

DDR5 commonly runs Gear 2.

6. RAM Timings Explained

Timings are memory delays measured in cycles.

Lower = better latency.

Example:

32-38-38-96

These are:

tCL
tRCD
tRP
tRAS
7. Primary Timings
tCL (CAS Latency)

Delay before data access.

Lower improves latency most.

tRCD

Delay between row and column access.

Often hardest timing to lower.

tRP

Time needed to close row before opening another.

tRAS

Minimum row active time.

Usually:

tRAS = tCL + tRCD + small margin
8. Secondary Timings

Second-level delays.

Huge performance impact.

Important Secondary Timings
Timing	Purpose
tRFC	Refresh cycle
tRRD_S/L	Row activation delays
tFAW	Four activate window
tWR	Write recovery
tWTR_S/L	Write-to-read delay
tCWL	CAS write latency
tREFI	Refresh interval
tRFC

Most impactful secondary timing.

Lower:

improves latency
improves responsiveness

Too low:

instability
memory corruption
tREFI

Higher:

better performance
less refreshing

Too high:

instability from heat
9. Tertiary Timings

Fine-tuning delays.

Smaller gains individually, large combined gains.

Common tertiaries:

Timing	Purpose
tRDRD	Read-to-read
tWRWR	Write-to-write
tRDWR	Read-to-write
tWRRD	Write-to-read

These primarily improve:

bandwidth efficiency
responsiveness
gaming smoothness
10. Voltages Explained
DRAM Voltage (VDIMM)

Main RAM voltage.

Typical:

DDR4: 1.35V
DDR5: 1.1–1.45V
SOC Voltage (AMD)

Feeds memory controller.

Safe daily:

Ryzen 7000/9000: ~1.20–1.30V

Avoid excessive SOC.

VDD / VDDQ

DDR5 memory voltages.

Usually:

1.25–1.45V
IMC Voltage

Intel memory controller voltage.

Can improve:

high-frequency stability
Gear 1 stability
11. Memory IC (Die) Types

The memory IC matters more than branding.

Samsung B-Die

Best DDR4 IC.

Characteristics:

scales with voltage
tight timings
amazing latency

Typical:

3200 CL14
3600 CL14

Great for:

esports gaming
low latency tuning
Hynix DJR

Frequency-focused DDR4.

Good:

high clocks
decent timings
Hynix A-Die

Best overall DDR5 IC.

Characteristics:

insane scaling
7000–8600+
excellent stability

Most premium DDR5 uses A-Die.

Hynix M-Die

Older DDR5 Hynix IC.

Still excellent.

Micron Rev E

Good DDR4 frequency scaling.

Weaker latency.

Samsung DDR5

Generally weaker than Hynix DDR5.

12. How to Identify Your RAM Die

Tools:

Thaiphoon Burner
ZenTimings
CPU-Z

You can also:

search part number online
use community databases
13. AMD RAM Overclocking
Best Practices
Ryzen 5000 DDR4

Sweet spot:

3600 CL14
FCLK 1800
Ryzen 7000/9000 DDR5

Sweet spots:

6000 CL30
6200 CL28/30
6400 if stable

Keep:

UCLK=MCLK when possible
Important AMD BIOS Settings
Setting	Recommended
EXPO	Enabled
Memory Context Restore	Enabled after stable
Power Down Enable	Disabled
Gear Down Mode	Depends
FCLK	Manually tuned
14. Intel RAM Overclocking
DDR4

Intel usually handles:

higher frequencies
Gear 1 flexibility

Common:

4000 CL15
4400 CL16
DDR5

Intel dominates extreme DDR5 frequency.

Common:

7600+
8200+
9000+ on Apex boards
15. BIOS Navigation Guide

Common motherboard tabs:

Brand	Section
MSI	OC
ASUS	AI Tweaker
Gigabyte	Tweaker
ASRock	OC Tweaker
16. Step-by-Step Overclocking Workflow
Step 1 — Enable XMP/EXPO

Always start here.

Step 2 — Stability Test

Run:

TM5
Karhu
OCCT

Verify baseline.

Step 3 — Increase Frequency

Example:

6000 → 6200 → 6400
Step 4 — Increase Voltage

Small increments:

0.01–0.03V
Step 5 — Tighten Timings

Primary first.
Then secondary.
Then tertiary.

17. Stability Testing
Essential Tools
TestMem5 (TM5)

Best quick stability tool.

Use:

anta777 config
absolut config
Karhu RAM Test

Excellent detection.

OCCT

Good mixed stability.

Recommended Durations
Test	Duration
Quick Check	20–30 min
Daily Stable	2–4 hrs
Hardcore Stable	8–12 hrs
18. Error Diagnosis
Symptom	Likely Cause
Instant crash	Voltage too low
WHEA errors	IMC instability
BSOD after idle	SOC issue
Errors after heat	tREFI too high
Training failure	Frequency too high
19. Safe Voltage Limits
DDR4
Voltage	Safe Daily
DRAM	1.45–1.50V
SOC	≤1.15V
DDR5
Voltage	Safe Daily
VDD/VDDQ	1.45V
SOC	1.30V
IMC	Depends CPU

Cooling matters heavily.

20. Timing Tightening Strategy

Order:

tCL
tRCD
tRP
tRAS
tRFC
tREFI
tRRD
tFAW
tertiaries
21. Frequency Scaling Strategy
Gaming

Usually:

lower latency > max frequency
Productivity

Usually:

bandwidth matters more
22. Command Rate & Gear Down Mode
Command Rate
Setting	Meaning
1T	Faster
2T	Easier stability
Gear Down Mode

AMD feature.

Can improve:

stability

Can worsen:

latency slightly
23. PMIC Unlocking (DDR5)

Some DDR5 kits:

locked PMIC
unlocked PMIC

Unlocked:

higher voltage control
better OC potential
24. Cooling & Thermal Management

RAM temperature matters.

Especially:

DDR5
high tREFI
high voltage

Recommended:

airflow across DIMMs
avoid stagnant air
25. Benchmarking
Useful Tools
AIDA64
y-cruncher
CapFrameX
Important Metrics
Metric	Importance
Read bandwidth	General throughput
Write bandwidth	Productivity
Copy bandwidth	Memory efficiency
Latency	Gaming responsiveness
26. Example Configurations
Ryzen 7800X3D + Hynix A-Die
DDR5-6000
30-36-36-76
UCLK=MCLK
FCLK 2000
1.40V
Intel 14900K + A-Die
DDR5-7600
34-45-45-110
1.45V
Gear 2
Ryzen 5800X3D + B-Die
DDR4-3800
14-14-14-28
FCLK 1900
1.50V
27. Advanced Tuning
RTL/IOL Training

Advanced Intel latency tuning.

Can significantly reduce latency.

Memory Training Algorithms

BIOS retrains memory each boot.

Training instability:

causes long boot times
random instability
CAD Bus Settings

AMD signal integrity tuning.

Includes:

ProcODT
RTT values
Drive strengths

Advanced only.

28. Troubleshooting
System Won’t Boot
Clear CMOS
Boot with one stick
Lower frequency
Raise voltage slightly
Random Game Crashes

Usually:

memory instability
SOC instability
overheating
Stuttering

Potential causes:

unstable FCLK
unstable tertiaries
Gear mode issues
29. Common Myths
“Higher MHz always wins”

False.

Latency matters heavily.

“More voltage always helps”

False.

Too much voltage:

increases heat
worsens stability
“MemTest passing means stable”

False.

Different tests catch different errors.

30. Recommended Tools
Monitoring
HWInfo64
ZenTimings
Stability
TM5
Karhu
OCCT
y-cruncher
BIOS Databases
Overclock.net
Reddit r/overclocking
31. Glossary
Term	Meaning
IMC	Integrated Memory Controller
IC	Memory chip/die
MCLK	Memory clock
UCLK	Memory controller clock
FCLK	Infinity Fabric clock
PMIC	Power Management IC
Training	Memory initialization process
POST	Power-on self test
WHEA	Hardware error reporting
32. Final Notes

Good RAM tuning is:

patience
testing
small changes
understanding interactions

The biggest gains usually come from:

tightening tRFC
optimizing secondaries
stable UCLK/FCLK
lowering latency overall

For gaming:

stable low latency usually beats raw frequency.
Community Resources
DDR4 OC Bible

Integralfx DDR4 OC Guide

DDR5 Community Info

Buildzoid YouTube

RAM Timing Calculator

Notkyon DDR5 Calculator
