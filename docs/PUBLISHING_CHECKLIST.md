# Google Play Store & Amazon Appstore Publishing Checklist

Use this checklist to prepare the on-device AI app for submission to both Google Play and Amazon Appstore. All items should be completed per-release.

## Technical Readiness
- [ ] Produce signed **Android App Bundle (AAB)** for Play and **APK** or **AAB** for Amazon using release keystore stored securely.
- [ ] Configure **applicationId** suffixes/flavors: `playRelease` and `amazonRelease` with store-specific dependencies guarded by flavor dimensions.
- [ ] Verify supported ABIs (arm64-v8a, armeabi-v7a, x86_64 if needed) and minSdkVersion 26+.
- [ ] Enable **Play App Signing** (Play) or provide signed binaries (Amazon) with the same keystore each release.
- [ ] Confirm **ProGuard/R8** rules for native libraries (`llama.cpp`, `onnxruntime`) and JNI are correct.
- [ ] Validate background downloads via **WorkManager** continue with battery/network constraints and respect Data Saver.
- [ ] Ensure offline functionality works after first-run downloads (airplane mode test).

## Privacy, Security & Compliance
- [ ] Provide an **in-app Privacy Policy** view and link to hosted policy URL in store listings.
- [ ] Data Safety (Play) & privacy questionnaire (Amazon): declare on-device processing and any optional online services; note that model downloads are stored locally.
- [ ] Request runtime permissions contextually (microphone, camera, notifications if used); include rationales.
- [ ] Sign and checksum-verify all agent/model bundles; block unsigned or tampered files.
- [ ] Ensure no third-party SDKs collect PII without consent; offer analytics opt-in/out toggles.
- [ ] Include content safety guardrails and a **user-facing safety disclaimer**.
- [ ] Verify export compliance (encryption) declarations.

## UX & Accessibility
- [ ] Complete onboarding that explains storage impact, offline processing, and how to download agents.
- [ ] Provide **agent catalog** with download progress, pause/resume, and storage management.
- [ ] Support **TalkBack** labels, large font sizes, and color contrast requirements.
- [ ] Localize core strings and store listing text; verify RTL layouts.
- [ ] Include crash-free flow for devices with limited RAM; show recommendations for lightweight models.

## Testing & QA
- [ ] Automated tests: unit tests for agent management, integration tests for downloads, UI tests for onboarding and chat.
- [ ] Manual smoke on low-end and high-end devices/emulators; verify cold start and inference latency.
- [ ] Run **Google Play pre-launch report** and fix security/ANR/crash issues.
- [ ] Verify Amazon-specific behaviors: in-app review alternative, entitlement/billing replacements if used.

## Store Listing Assets
- [ ] Adaptive **app icon** (Google Play) and required icon sizes for Amazon.
- [ ] **Feature graphic** (Play), **screenshots** (phone/tablet), and **short promo video** if available.
- [ ] Short and long **descriptions** focusing on on-device privacy, agent catalog, and offline capabilities.
- [ ] **Content rating** questionnaires completed.
- [ ] **Support contact** (email/website) included.

## Release & Rollout
- [ ] Set up **closed testing** tracks (Play) and Amazon **Live App Testing**; gather feedback before production.
- [ ] Use **staged rollout** on Play; monitor ANRs/crashes/ratings before 100% release.
- [ ] Maintain changelog/release notes per version.
- [ ] Archive artifacts and checksums for reproducibility.

Keep this checklist updated as features evolve. Mark each item complete before submitting a release.
