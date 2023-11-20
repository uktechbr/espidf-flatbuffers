![logo](http://google.github.io/flatbuffers/fpl_logo_small.png) FlatBuffers
===========

**FlatBuffers** is a cross platform serialization library architected for
maximum memory efficiency. It allows you to directly access serialized data without parsing/unpacking it first, while still having great forwards/backwards compatibility.

Reference: https://github.com/google/flatbuffers

## Quick Start

1. Import esp-idf flatbuffers into your project

    ```
    idf.py add-dependency "uktech/espidf-flatbuffers^23.5.26"
    ```

2. Define your flatbuffer schema (`.fbs`)

    Write the [schema](https://flatbuffers.dev/flatbuffers_guide_writing_schema.html) to define the data you want to serialize. See [monster.fbs](https://github.com/google/flatbuffers/blob/master/samples/monster.fbs) for an example.

3. Generate code for your language(s)

    Use the `flatc` compiler to take your schema and generate language-specific code:

    ```
    ./flatc --cpp monster.fbs
    ```
    
    Which generates `monster_generated.h` file.

4. Serialize data

    Use the generated code, as well as the `FlatBufferBuilder` to construct your serialized buffer. ([`C++` example](https://github.com/google/flatbuffers/blob/master/samples/sample_binary.cpp#L24-L56))

5. Transmit/store/save Buffer

    Use your serialized buffer however you want. Send it to someone, save it for later, etc...

6. Read the data

    Use the generated accessors to read the data from the serialized buffer.
    
    It doesn't need to be the same language/schema version, FlatBuffers ensures the data is readable across languages and schema versions. See the [`Rust` example](https://github.com/google/flatbuffers/blob/master/samples/sample_binary.rs#L92-L106) reading the data written by `C++`.
