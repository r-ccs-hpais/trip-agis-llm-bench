# TRIP AGIS LLM BENCH

LLM training benchmark for TRIP AGIS system

This benchmark measures throughput of a causal language model training in tokens per second.

## Correctness

In order to be able to execute in relatively short time, the benchmark does not check for convergence to a given fidelity metric etc.
We expect that all operations are performed correctly in corresponding numeric formats, according to the model definition.
Correctness might be additionally checked by code review and test runs outside of benchmark.

## Numeric precision

Numeric precision used in the benchmark can be FP16, BF16 or any other format using more than 16 bits per value.


## Model

Submitters execute training of GPT-like model as defined by the job script `run_benchmark.sh`.
The actual parallelization scheme is not fixed in order to accommodate for different network topologies. The model size is set, however, to be prohibitively large for a typical stand-alone accelerator.

Reference implementation is based on Megatron-LM codebase and supports "tensor" and pipeline parallelism.


### Running

Download vocabulary file with `bash download_vocab.sh` in `data` subdirectory.

Dump corpus to jsonl format by running `python3 dump_wiki.py` and tokenize by running `preprocess.sh` script.

Modify `run_benchmark.sh` script to match target hardware and run.