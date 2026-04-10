# PIES - Official User Manual and Policy Whitepaper
*Pretty Isolated Encrypted System*

**By:** nulsie
**License:** GNU GPL v3

---

## 1. PURPOSE & TARGETED AUDIENCE
PIES is a cryptographic environment designed for users who require total digital sovereignty.

**Expected Users:**
* **Privacy Conscious Netizens:** Requiring storage with no network trail.
* **Journalists:** Operating in hostile environments needing "stealth" retro-styled tools.
* **Sovereignty Advocates:** Who reject SaaS models in favor of 100% local control.
* **High-Net-Worth Individuals:** Clients seeking a digital counterpart to a physical Swiss vault for sensitive logs or documentation.

---

## 2. PRIVACY AND SECURITY

### A. TECHNICAL INACCESSIBILITY AND ZERO-ACCESS POLICY
* **Total Data Inaccessibility:** PIES is architecturally a "Zero-Knowledge" system. Because the application operates entirely within your local browser's memory and storage, I do not—and technically cannot—have the data.
* **No Data Possession:** There is no central server, cloud database, or "PIES backend" where your files could be stored. Your Account ID, Passkey, and depository items remain exclusively on your own device; I have nothing to use, share, or lose.
* **Zero-Network Trail:** The application code contains zero network-bound instructions (no fetch or XMLHttpRequest calls). This ensures that your usage generates no digital metadata, making it impossible for the developers or ISP-level surveillance to monitor your activity.

### B. CRYPTOGRAPHIC AND FORENSIC FEATURES
* **Sovereign Encryption:** All data is locally encrypted using AES-256, while credentials are secured via one-way SHA-256 hashing with Salt and PBKDF2(100k) iterating system.
* **Volatile RAM Protection:** To protect against physical device seizure, PIES stores your active "Vault Key" (the unhashed passkey) only in volatile RAM. Logging out or refreshing the browser instantly purges the key, ensuring that no readable data remains in the computer's memory.
* **The Duress Passkey:** The Duress Passkey acts as a hidden emergency kill-switch. It is a secondary password set up during registration. When used, the app identifies the specific duress hash. It instantly wipes the document array from local storage. This irreversibly deletes all encrypted files and titles. The process is silent and happens during the login flow. The user is then logged into a completely empty vault. It provides plausible deniability by hiding all evidence. Your data is destroyed to keep it from being discovered.
* **No Backdoor Infrastructure:** By design, PIES omits a "Forgot Password" or account recovery feature. This ensures that no third party, including the developers, can ever bypass your encryption to access your files.

---

## 3. TECHNICAL BLUEPRINT: ZERO-KNOWLEDGE
The entire PIES application is contained within a single HTML file. This architecture is a deliberate security choice known as a Static Local Environment.

### A. LOCAL-ONLY EXECUTION
PIES operates as a single-file static HTML environment. It generates zero network traffic, ensuring ISPs cannot detect when the vault is accessed.

### B. CRYPTOGRAPHIC STANDARDS
* **AES-256:** Every character entered is transformed into ciphertext using the user's Passkey.
* **SHA-256 Hashing:** Credentials are protected by one-way hashing; the original password is never stored in readable form.
* **Salt in Hashing:** Salting is a security technique that adds a unique string of random data—a "salt"—to your passkey before it is hashed and stored. In this application, a unique salt is generated for every user during registration, ensuring that even if two people use the exact same passkey, their stored hashes and encryption keys will look completely different. This process prevents attackers from using "Rainbow Tables" (pre-computed lists of common passwords) to crack your vault. By forcing the system to calculate a unique result for every single account, salting ensures that an attacker cannot use work done on one account to compromise another.
* **PBKDF2 100k Iterations Layering with Encryption:** PBKDF2 with 100k iterations is the vault's core security engine. It transforms your simple passkey into a high-strength encryption key. The process uses a unique "salt" to prevent pre-computed crack attacks. By running the hashing algorithm 100,000 times, it adds a massive time cost. This "computational work" makes brute-force guessing extremely slow and difficult. Even powerful computers struggle to test many passwords against this barrier. It ensures that your data remains locked even if the file is stolen. The 100k count is a standard balance between high security and speed. This turns a human password into a machine-grade cryptographic shield.

### C. VOLATILE RAM PROTECTION
The unhashed "Vault Key" exists only in the device's RAM while the session is active. Refreshing the page or clicking "Logout & Lock" instantly purges the key from memory.

---

## 5. OPERATIONAL PROCEDURES: THE NEED OF THE PHYSICAL "AIR GAP" PROCEDURE

> **WARNING: LOSS OF PASSKEY RESULTS IN PERMANENT DATA DESTRUCTION.**

**PIES deliberately omits a "Forgot Password" feature because any recovery mechanism is a security vulnerability.**

**The Official "Physical Storage" Protocol for Storing Your PIES Passkey:**
* **Avoid Digital Password Managers:** Do not store your PIES Passkey in any cloud-based or digital password manager.
* **Physical Inscription:** Write your Account ID and Passkey on a durable physical medium.
* **Metal Engraving:** For maximum longevity, engrave your credentials on a stainless steel or titanium plate to ensure the key survives fire, flood, or magnetic interference. Or you could simply use a laminated fireproof paper.
* **Vault Storage:** Place this physical key in a fireproof locker or physical safe of your choosing.

---

## 6. SAFE BROWSER PROTOCOLS
While the PIES protocol is secure, the browser environment can be a weak point. Users are advised to the following:
* **Always Use Incognito Mode:** Prevents the browser from saving cached fragments of unencrypted data.
* **Try Using Privacy Browsers:** Use LibreWolf, Mullvad, or Brave (Max Shields).
* **Extension Audit:** Disable all extensions to prevent screen-scraping or keylogging.

---

## 7. How to Use PIES
* **Prepare a Secure Browser Environment:** Before launching the file, ensure you are using a privacy-focused browser like LibreWolf, Mullvad, or Brave (optional for civilian users). It is mandatory for high-risk users to operate in Incognito/Private Mode and to use a privacy focused browser to prevent the browser from saving cached fragments of unencrypted data, and all extensions should be disabled to mitigate keylogging risks.
* **Initialize the Secure Terminal:** Open the PIES.html file in your browser. The system requires a 10-second initialization period, during which you will see a loading bar. This delay is a deliberate protocol to ensure the secure data deposit environment is fully isolated and ready before any decryption occurs.
* **Register with Permanent Credentials:** Select the REGISTER tab to create your account by entering a unique Account ID and a complex Passkey. Note that PIES utilizes SHA-256 hashing for these credentials; because there is no central server, there is no "Forgot Password" feature. If you lose these credentials, your data is mathematically destroyed and unrecoverable.
* **Execute the Physical "Air-Gap" Protocol:** Immediately after registration, you must move your credentials to a physical medium. The manual mandates Physical Inscription—writing your ID and Passkey down—and recommends Metal Engraving on stainless steel or titanium to survive environmental disasters. Store this physical key in a fireproof vault or safe; never save it in a digital or cloud-based password manager.
* **Manage and Encrypt Depository Items:** Once logged in, you can create a NEW ITEM or UPLOAD existing text files. Every character you type is transformed into AES-256 ciphertext in real-time. The application features a 10-second "Auto-save heartbeat" that automatically encrypts and persists your data to the local browser storage, but you can also manually click EXECUTE SAVE (PERSIST) at any time.
* **Securely Terminate the Session:** When your work is complete, click LOGOUT & LOCK or simply refresh the browser page. This triggers the Volatile RAM Purge, which instantly deletes the unhashed decryption key from your computer’s memory. This anti-forensic measure ensures that no readable data remains in the RAM if the device is seized or inspected after the session.

---
*By using PIES, you are the only person on Earth with the keys to this safe.*