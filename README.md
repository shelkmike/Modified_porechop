The original Porechop (https://github.com/rrwick/Porechop) has an embedded list of adapters, thereby not allowing a user to provide a custom list of adapters. <b>Modified_porechop</b> fixes this shortcoming. Basically, it works in the same way as Porechop, but has an additional parameter "--adapters", which allows a user to provide a FASTA file with adapter sequences.

### Installation

`git clone https://github.com/shelkmike/Modified_porechop.git`<BR>
`cd Modified_porechop`<BR>
`python3 setup.py install`<BR>
<BR>
To test whether Modified_porechop has been installed, type
`modified_porechop --help`

### Usage
For all details not related to the <i>--adapters</i> option, see the manual for the original Porechop (https://github.com/rrwick/Porechop).

The option <i>--adapters</i> requires a FASTA file which should be formatted in the following way:<BR>
\>Some_adapter|left<BR>
AAGCAGTGGTATCAACGCAGAGT<BR>
\>Some_adapter|right<BR>
ACTCTGCGTTGATACCACTGCTT<BR>
\>Some_other_adapter|right<BR>
GTTGATACCACTGC<BR>

The title for each sequence consists of two parts: the one before "|" and the one after. The part before "|" is a name of the adapter. The part after "|" indicates whether this adapter can occur on the left end of a read or on the right end of a read. If some adapter can be on either end, provide its sequence twice. In the above example, "Some_adapter" can be on either end, and, naturally, its right sequence is a reverse complement of its left sequence. "Some_other_adapter" in this example is expected only on the right end of a read, hence there is no "|left" counterpart for it.

A comprehensive set of Nanopore adapters (adapters.fasta) is provided with the Modified_porechop. It is a slightly extended version of the set provided with the classic Porechop.<BR><BR>
Caveat: currently, Modified_porechop can utilize any non-barcoding (i.e. not containing a barcode) adapters provided by the user, but it can use only the standard set of Nanopore barcoding adapters (see them with titles like "BC19" in adapters.fasta). If you would like Modified_porechop to be able to use some non-standard barcoding adapters, let me know via Issues (https://github.com/shelkmike/Modified_porechop/issues).
