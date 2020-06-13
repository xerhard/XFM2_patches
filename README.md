# XFM2_patches
json patch files for the XFM2

The json file format is easy to understand.
Main part is just Par#:value for all parameters.

Main advantage of the json file is you are free to expand it as long as the **parameters** part is intact you can use the json file to upload a patch to the XFM2

Second interesting use is you could only put a selection of the  parameters in a json file so only these parameters are overwritten when uploaded to the XFM2. 

In the **patches/DX7_algorithms** folder you find the patches to set the operators according the 32 DX7 algorithms.
Other usage is to create effects presets, see **patches/effects**

## patches overview

- **DX7.syx**: DX7 presets used for creation of DX7_Converted
- **DX7_algorithms**:  settings to mimic 32 DX7 algorithms
- **DX7_converted**: conversion of DX7 libraries to XFM2 patches (not foolproof yet, but often close)
- **XFM2_1.02presets**: some presets as set in 1.02
- **effects**: example of usage subset of parameters 


## Remarks

### hash
hash field is used as fingerprint, while the XFM2 does not have an option to save patch names, the hashes can be used to recognise (sub-)patches. While the value of the hash is meaningless I chose to present it in hex. Calculation of the hash value is done with `java.util.Arrays.hashCode` as in [XFM2_GetterSetter](https://github.com/xerhard/XFM2_GetterSetter)

Source code of the hash algorithm can be found on [link to original source of java.util.Arrays.hashCode](https://hg.openjdk.java.net/jdk8/jdk8/jdk/file/tip/src/share/classes/java/util/Arrays.java)

Code snippet can easily be converted to any other programming language:

	public static int hashCode(long a[]) {
	        if (a == null)
	            return 0;
	
	        int result = 1;
	        for (long element : a) {
	            int elementHash = (int)(element ^ (element >>> 32));
	            result = 31 * result + elementHash;
	        }
	
	        return result;
	    }

